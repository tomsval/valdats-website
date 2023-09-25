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
    <p class="title">valdats.id.lv</p>
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
    @import url('https://fonts.googleapis.com/css2?family=Flow+Circular&family=Sono:wght@400;500&display=swap');

    .title {
        font-family: "Flow Circular", sans-serif;
        font-size: 24pt;
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
        font-family: "Sono", Courier, monospace;
        font-weight: 500;
        font-size: 72pt;
    }

    .date-display {
        font-family: "Sono", Courier, monospace;
        font-weight: 400;
        font-size: 32pt;
    }
</style>