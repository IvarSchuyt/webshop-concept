<script>
    import { onMount } from 'svelte';

    // Array to hold references to the span elements
    let spanElements = [];

    // Function to move a span element to a random position and make it visible
    function moveSpan(spanElement) {
        const randomX = Math.random() * window.innerWidth;
        const randomY = Math.random() * window.innerHeight;

        spanElement.style.left = `${randomX}px`;
        spanElement.style.top = `${randomY}px`;
        spanElement.style.display = 'block';

        setTimeout(() => {
            spanElement.style.display = 'none';
        }, 200);
    }

    // Function to set intervals for each span element
    function setIntervals() {
        spanElements.forEach((spanElement, index) => {
            setInterval(() => {
                moveSpan(spanElement);
            }, 2000 + index * 500); // Different intervals for each span
        });
    }

    onMount(() => {
        setIntervals();
    });

    onMount(() => {
        const audio = new Audio('beat.mp3');
        audio.loop = true;
        audio.play();
    });
</script>

<section>
    <header>
        <a href="/"><h1>イシュ</h1></a>
    </header>

    <ul>
        <li>
            <div>
                <img src="1.webp" alt="">
            </div>
            <span>セーター</span>
        </li>
        <li>
            <div>
                <img src="3.webp" alt="">
            </div>
            <span>Tシャツ</span>
        </li>
        <li>
            <div>
                <img src="4.webp" alt="">
            </div>
            <span>Tシャツ</span>
        </li>
        <li>
            <div>
                <img src="5.webp" alt="">
            </div>
            <span>Tシャツ</span>
        </li>
        <li>
            <div>
                <img src="2.webp" alt="">
            </div>
            <span>セーター</span>
        </li>
        <li>
            <div>
                <img src="6.webp" alt="">
            </div>
            <span>Tシャツ</span>
        </li>
    </ul>

    <!-- Multiple span elements with class popup -->
    {#each Array(5) as _, i}
        <span class="popup" bind:this={spanElements[i]}>イシュ</span>
    {/each}
</section>

<style>
    header {
        padding: 2rem 0;
    }

    a {
        text-decoration: none;
    }

    h1 {
        font-size: 2rem;
    }

    section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }

    ul {
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        gap: 2.5rem 5rem;
    }

    li {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1rem;
    }

    div {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 20rem;
        width: 20rem;
        overflow: hidden;
    }

    img {
        height: 130%;
        width: 130%;
        object-fit: cover;
    }

    .popup {
        position: absolute;
        display: none;
        z-index: -1;
    }
</style>