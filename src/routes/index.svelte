<script>
    import Title from '$lib/Title.svelte';
    import Search from '$lib/Search.svelte';
    import InfoCard from '$lib/InfoCard.svelte';
    import Map from '$lib/Map.svelte';
</script>

<svelte:head>
    <title>Frontend Mentor | IP Address Tracker</title>
</svelte:head>

<header>
    <Title />

    <Search />

    <InfoCard />
</header>

<Map />

<style>
    header {
        background: url('pattern-bg.png') no-repeat center bottom royalblue;
        background-size: cover;
        padding: 1.625rem 1.5rem;
        height: 300px;
        position: relative;
        z-index: 10000;
    }
</style>
