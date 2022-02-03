<script>
    import Title from '$lib/Title.svelte';
    import Search from '$lib/Search.svelte';
    import InfoCard from '$lib/InfoCard.svelte';
</script>

<svelte:head>
    <title>Frontend Mentor | IP Address Tracker</title>
</svelte:head>

<header>
    <Title />

    <Search />

    <InfoCard />
</header>

<style>
    header {
        background: url('pattern-bg.png') no-repeat center bottom royalblue;
        background-size: cover;
        padding: 1.625rem 1.5rem;
        height: 300px;
    }
</style>
