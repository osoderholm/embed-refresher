<script lang="ts">
    let url: string = "";
    let seconds: number = 0;
    let zoom: number = 100;

    $: result = `${location.origin}/?url=${encodeURIComponent(url)}&refresh=${seconds}&zoom=${zoom}`;
</script>

<div class="root">
    <div class="info">
        <h1>Embed Refresher</h1>
        <p>Specify the URL and the refresh interval. The resulting link will show the URL and refresh it automatically.</p>
        <p>Useful for situations where a page does not automatically refresh its contents.</p>
        <p>Keep in mind that the embedded pages must allow embedding (<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options">X-Frame-Options</a>)</p>
        <p><strong>NEW!</strong> You can now specify a zoom level. This only works on some sites.</p>
    </div>
    <div class="form">
        <label>
            URL
            <input type="url" bind:value={url}>
        </label>
        <label>
            <span>Refresh timeout (seconds)</span>
            <span>(0 seconds = no refreshing)</span>
            <input type="number" min=0 bind:value={seconds}>
        </label>
        <label>
            Zoom %
            <input type="number" min=1 max="500" bind:value={zoom}>
        </label>
    </div>
    {#if url.length > 0 && seconds >= 0 && zoom > 0}
        <div class="result">
            <p>Here is your link:</p>
            <a target="_blank" href={result} >{result}</a>
        </div>
    {/if}
    <div class="links">
        <div>Source code on <a href="https://github.com/osoderholm/embed-refresher">GitHub</a></div>
        <div>Icons made by <a href="https://www.flaticon.com/authors/juicy-fish" title="juicy_fish">juicy_fish</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
    </div>
</div>

<style>
    .root {
        text-align: center;
        padding: 1em;
        max-width: 500px;
        margin: 0 auto;
        display: flex;
        flex-flow: column;
    }
    .form {
        display: flex;
        flex-flow: column;
    }
    .result {
        margin-top: 1rem;
    }
    .form label {
        display: flex;
        flex-flow: column;
        max-width: 300px;
        align-self: center;
        width: 100%;
    }
    .links {
        margin-top: 10rem;
        font-size: 8pt;
    }
</style>
