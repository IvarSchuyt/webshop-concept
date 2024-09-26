<script>
    import { onMount } from 'svelte';

    // Reference to the span element
    let spanElement;

    // Function to run when the component is mounted
    onMount(() => {
        // Set an interval to move the span element every 200ms
        setInterval(() => {
            // Generate random x and y positions within the window
            const randomX = Math.random() * window.innerWidth;
            const randomY = Math.random() * window.innerHeight;
            
            // Set the position of the span element
            spanElement.style.left = `${randomX}px`;
            spanElement.style.top = `${randomY}px`;
            
            // Make the span element visible
            spanElement.style.display = 'block';

            // Hide the span element after 200ms
            setTimeout(() => {
                spanElement.style.display = 'none';
            }, 200);
        }, 2000);
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

    <span class="popup" bind:this={spanElement}>イシュ</span>

</section>



<style>

    header{
        padding: 2rem 0;
    }
    
    a{
        text-decoration: none;
    }

    h1{
        font-size: 2rem;
    }
    
    section{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }

    ul{
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        gap: 2.5rem 5rem;
    }

    li{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1rem;
    }

    div{
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