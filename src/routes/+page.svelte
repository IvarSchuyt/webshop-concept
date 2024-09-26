<script>
    let video;
    let showButton = true;

    function playVideo() {
        video.play();
        showButton = false;
    }

    function handleVideoEnd() {
        window.location.href = '/shop'; // Change this to the URL you want to navigate to
    }
</script>

<section>
{#if showButton}
    <button on:click={playVideo}>入力</button>
{/if}

<video bind:this={video} src="intro.mp4" preload="auto" on:ended={handleVideoEnd}>
    <track kind="captions">
</video>
</section>

<style>
    section {
        position: relative;
        width: 100%;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    button {
        background-color: #4CAF50;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        position: absolute;
        z-index: 1;
    }

    video {
        height: 100vh;
    }
</style>