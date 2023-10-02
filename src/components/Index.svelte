<script lang="ts">
    import { onMount } from "svelte";

    // NTP time experiment
    // import { Client } from "ntp-time";

    // const ntp_client = new Client("0.pool.ntp.org", 123, { timeout: 5000 });

    // async function sync_ntp(): Promise<void> {
    //     try {
    //         await ntp_client.syncTime();
    //     } catch (err) {
    //         console.log(err);
    //     }
    // }

    // $: {    
    //     (async() => {
    //         await sync_ntp();
    //         const ntp_time = async () => {
    //             ntp_client.syncTime()
    //             .then(time => {
    //                 return time;
    //             })
    //             .catch(console.log)
    //         }
    //         const ntp_date = await ntp_time();
    //         console.log(ntp_date);

    //     });
    // }

    // Local time
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
            console.log(time.getMonth());
        }, 1000);

        return () => {
            clearInterval(interval);
        };
    });
</script>

<div class="index-component">
    <p class="time-display">
        {h} : {m} . {s}
    </p>
    <div class="break"></div>
    <p class="date-display">
        {yyyy} - {mm + 1} - {dd}
    </p>
    <div class="break"></div>
    <p class="title">valdats.id.lv</p>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Flow+Circular&family=Sono:wght@400;500&display=swap');

    .title {
        font-family: "Flow Circular", sans-serif;
        font-size: 2vw;
    }

    .index-component {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: center;
    }

    .break {
        flex-basis: 100%;
        height: 2vw;
    }

    .time-display {
        font-family: "Sono", Courier, monospace;
        font-weight: 500;
        font-size: 6vw;
    }

    .date-display {
        font-family: "Sono", Courier, monospace;
        font-weight: 400;
        font-size: 5vw;
    }
</style>