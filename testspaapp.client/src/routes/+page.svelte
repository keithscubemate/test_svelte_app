<script lang='ts'>
    import { onMount } from "svelte";

    interface Forecast {
        date: string;
        temperatureC: number;
        temperatureF: number;
        summary: string;
    }

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
            <p>{date} [{temperatureC} -- {temperatureF}]: {summary}</p>
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

/* Style individual list items */
li {
    background-color: #f9f9f9; /* Light gray background */
    border: 1px solid #ddd; /* Subtle border */
    border-radius: 8px; /* Rounded corners */
    padding: 15px; /* Spacing inside each item */
    margin-bottom: 10px; /* Spacing between items */
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Soft shadow */
}

/* Style paragraph inside list items */
li p {
    font-family: 'Arial', sans-serif; /* Clean font */
    font-size: 16px; /* Readable font size */
    color: #333; /* Text color */
    margin: 0; /* Remove default paragraph margin */
}

/* Add hover effect for list items */
li:hover {
    background-color: #eaf5ff; /* Light blue background on hover */
    border-color: #cce7ff; /* Slightly darker border on hover */
    cursor: pointer; /* Indicate interactivity */
    transition: background-color 0.3s ease, border-color 0.3s ease; /* Smooth animation */
}

/* Responsive design for smaller screens */
@media (max-width: 600px) {
    li {
        font-size: 14px; /* Slightly smaller font size */
        padding: 10px; /* Adjust padding */
    }
}
</style>
