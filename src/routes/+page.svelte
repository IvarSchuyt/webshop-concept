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

    function skipVideo() {
        video.pause();
        handleVideoEnd();
    }
</script>

<section>
{#if showButton}
    <button on:click={playVideo}>入力</button>
{/if}
<button on:click={skipVideo} class="skip">Skip</button>

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
        background-color: transparent;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        position: absolute;
        z-index: 1;
        scale: 1.25;
    }

    .skip{
        background-color: #9ea29e;
        scale: 1;
        position: absolute;
        top: 1rem; 
        right: 1rem;
    }

    button:not(.skip)::before{
        content: '';
        clip-path: polygon(17% 26%, 88% 29%, 94% 54%, 7% 66%);
        background-color: #9ea29e;
        position: absolute;
        top: -2rem;
        left: -2rem;
        width: 10rem;
        height: 8rem;
        z-index: -1;
        transition: 200ms ease-out;
    }

    button:hover::before{
        clip-path: polygon(16% 32%, 91% 27%, 94% 62%, 15% 50%);
    }

    video {
        height: 100vh;
    }
</style>