<script>
    import Index from "./components/Index.svelte";
    import Embed from "./components/Embed.svelte";

    const searchParams = new URLSearchParams(location.search);

    const url = searchParams.get("url");
    const seconds = searchParams.get("refresh");

</script>

<main>
    {#if url && url.length > 0 && seconds && seconds > 0}
        <Embed url={url} timeout={seconds}/>
    {:else}
        <Index/>
    {/if}
</main>

<style global>
    body {
        padding: 0;
        margin: 0;
    }
</style>
