<script>
    import Search from '$lib/Search.svelte';
</script>

<svelte:head>
    <title>Frontend Mentor | IP Address Tracker</title>
</svelte:head>

<header>
    <h1>
        <a href="/">IP Address Tracker</a>
    </h1>

    <Search />

    <div>
        <p>IP Address</p>

        <p>Location</p>

        <p>Timezone</p>

        <p>UTC</p> <!-- add offset value dynamically using the API -->
        
        <p>ISP</p>
    </div>
</header>

<style>
    header {
        background: url('pattern-bg.png') no-repeat center bottom royalblue;
        background-size: cover;
        padding: 1.625rem 1.5rem;
    }

    h1 {
        font-size: 1.625rem;
        font-weight: 500;
        text-align: center;
        margin-top: 0;
        margin-bottom: 1.75rem;
    }

    a {
        display: block;
        color: white;
    }
</style>
