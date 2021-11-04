<script lang="ts">
    let url: string = "";
    let seconds: number = 0;

    $: result = `${location.origin}/?url=${encodeURIComponent(url)}&refresh=${seconds}`;
</script>

<div class="root">
    <div class="info">
        <h1>Embed Refresher</h1>
        <p>Specify the URL and the refresh interval. The resulting link will show the URL and refresh it automatically.</p>
        <p>Useful for situations where a page does not automatically refresh its contents.</p>
        <p>Keep in mind that the embedded pages must allow embedding (<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options">X-Frame-Options</a>)</p>
    </div>
    <div class="form">
        <label>
            URL
            <input type="url" bind:value={url}>
        </label>
        <label>
            Refresh timeout (seconds)
            <input type="number" min=0 bind:value={seconds}>
        </label>
    </div>
    {#if url.length > 0 && seconds > 0}
        <div class="result">
            <p>Here is your refreshing link:</p>
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
    }
    .links {
        margin-top: 10rem;
        font-size: 8pt;
    }
</style>
