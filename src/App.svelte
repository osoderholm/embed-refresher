<script lang="ts">
    import Index from "./components/Index.svelte";
    import Embed from "./components/Embed.svelte";
    import {to_number} from "svelte/internal";

    const cfToken: string = process.env.CF_TOKEN;

    const searchParams: URLSearchParams = new URLSearchParams(location.search);

    const url: string = searchParams.get("url");
    const seconds: number = searchParams.get("refresh") ? to_number(searchParams.get("refresh")) : 0;

    const cfBeacon: string = `{"token": "${cfToken}"}`;

</script>

<main>
    {#if url && url.length > 0 && seconds && seconds > 0}
        <Embed url={url} timeout={seconds}/>
    {:else}
        <Index/>
    {/if}
</main>
{#if cfToken}
    <!-- Cloudflare Web Analytics -->
    <script defer src='https://static.cloudflareinsights.com/beacon.min.js' data-cf-beacon='{cfBeacon}'></script>
    <!-- End Cloudflare Web Analytics -->
{/if}

<style global>
</style>
