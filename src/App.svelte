<script lang="ts">
    import Index from "./components/Index.svelte";
    import Embed from "./components/Embed.svelte";
    import {to_number} from "svelte/internal";

    const searchParams: URLSearchParams = new URLSearchParams(location.search);

    const url: string = searchParams.get("url");
    const seconds: number = searchParams.get("refresh") ? to_number(searchParams.get("refresh")) : 0;

</script>

<main>
    {#if url && url.length > 0 && seconds && seconds > 0}
        <Embed url={url} timeout={seconds}/>
    {:else}
        <Index/>
    {/if}
</main>

<style global>
</style>
