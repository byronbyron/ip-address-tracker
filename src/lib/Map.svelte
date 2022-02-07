<script>
  import { onMount } from 'svelte';
  import { browser } from '$app/env';

  onMount(async () => {
    if (! browser) return;

    const leaflet = await import('leaflet');

    const apiKey = import.meta.env.VITE_API_KEY;
    const bypassCorsUrl = 'https://cors-anywhere.herokuapp.com/';
    const apiUrl = 'https://geo.ipify.org/api/v2/country,city';

    // elements to update
    let ip = document.getElementById('ip');
    let city = document.getElementById('city');
    let timeZone = document.getElementById('timeZone');
    let isp = document.getElementById('isp');

    // form elements 
    const searchInput = document.getElementById('searchInput');
    const searchBtn = document.getElementById('searchBtn');

    const headersOption = {
      headers: {
        'Access-Control-Allow-Origin': '*',
      }
    }

    const map = leaflet.map('map', {
      center: [0,0],
      zoom: 0,
      zoomControl: false,
      layers: [
        leaflet.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
          attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
        })
      ]
    }).setView([51.5, -0.09], 13);

    const updateMarker = (marker = [51.5, -0.09]) => {
      map.setView(marker, 13);
      leaflet.marker(marker).addTo(map);
    }

    const getIpDetails = (defaultIp) => {
      if (defaultIp == undefined) {
        var ipUrl = `${bypassCorsUrl}${apiUrl}?apiKey=${apiKey}`;
      } else {
        var ipUrl = `${bypassCorsUrl}${apiUrl}?apiKey=${apiKey}&ipAddress=${defaultIp}`;
      }

      fetch(ipUrl, headersOption)
        .then(results => results.json())
        .then(data => {
          ip.innerHTML = data.ip;
          city.innerHTML = `${data.location.city} ${data.location.country} ${data.location.postalCode}`;
          timeZone.innerHTML = data.location.timezone;
          isp.innerHTML = data.isp;

          updateMarker([data.location.lat, data.location.lng]);
        })
        .catch(error => {
          alert("Unable to get IP details");
          console.log(error);
        })
    }

    // document.addEventListener('load', updateMarker());

    searchBtn.addEventListener('click', e => {
      e.preventDefault();

      if (searchInput.value !== '' && searchInput.value !== null) {
        getIpDetails(searchInput.value);
        return;
      }

      alert("Please enter a valid IP address");
    })
  });
</script>

<svelte:head>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css" integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ==" crossorigin="" />

  <script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js" integrity="sha512-gZwIG9x3wUXg2hdXF6+rVkLF/0Vi9U8D2Ntg4Ga5I5BZpVkVxlJWbSQtXPSiUTtC0TjtGOmxa1AJPuV0CPthew==" crossorigin=""></script>
</svelte:head>

<div id="map" class="map"></div>

<style>
  @import 'https://unpkg.com/leaflet@1.7.1/dist/leaflet.css';

  .map {
    height: calc(100vh - 300px);
  }

  @media (min-width: 992px) {
    .map {
      height: calc(100vh - 280px);
    }
  }
</style>
