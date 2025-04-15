<script lang='ts'>
    import { onMount } from "svelte";
    import Weather from '$lib/Weather.svelte';

    let data = $state({})

    onMount(async () => {
        const response = await fetch('api/weatherforecast');

        data = await response.json(); // Parse JSON response

    })

</script>

<h1>Welcome to SvelteKit</h1>

<ul>
    {#each data as { date, temperatureC, temperatureF, summary }}
        <li>
            <Weather {date} {temperatureC} {temperatureF} {summary} />
        </li>
    {/each}
</ul>

<style>
    /* Apply styling to the list container */
ul {
    list-style: none; /* Remove default list styling */
    padding: 0; /* Remove padding */
    margin: 20px 0; /* Add vertical margin */
}
</style>
