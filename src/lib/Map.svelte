<script>
  import { onMount } from 'svelte';
  import { browser } from '$app/env';

  onMount(async () => {
    if(browser) {
      const leaflet = await import('leaflet');

      const map = leaflet.map('map').setView([51.505, -0.09], 13);

      leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
      }).addTo(map);

      leaflet.marker([51.5, -0.09]).addTo(map);
    }
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
</style>
