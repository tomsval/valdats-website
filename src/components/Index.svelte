<script lang="ts">
	import { onMount } from "svelte";

    let time = new Date();

    $: h = time.getHours();
    $: m = time.getMinutes();
    $: s = time.getSeconds();
    $: dd = time.getDate();
    $: mm = time.getMonth();
    $: yyyy = time.getFullYear();


    onMount(() => {
        const interval = setInterval(() => {
            time = new Date;
        }, 1000);

        return () => {
            clearInterval(interval);
        };
    });
</script>

<div class="index-component">
    <h1>valdats.id.lv</h1>
    <div class="break"></div>
    <p class="time-display">
        {h} : {m} . {s}
    </p>
    <div class="break"></div>
    <p class="date-display">
        {yyyy} - {mm} - {dd}
    </p>
</div>

<style>
    h1 {
        font-family: Arial, Helvetica, sans-serif;
    }

    .index-component {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: center;
    }

    .break {
        flex-basis: 100%;
        height: 2em;
    }

    .time-display {
        font-family: 'Courier New', Courier, monospace;
        font-weight: bold;
        font-size: large;
    }

    .date-display {
        font-family: 'Courier New', Courier, monospace;
        font-size: medium;
    }
</style>