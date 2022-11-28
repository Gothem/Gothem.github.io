<svelte:head>
    <title>Stefano Aguilera</title>
</svelte:head>

<script lang="ts">
    import { fade } from 'svelte/transition';
    import { onMount } from 'svelte';

    let preImgs = ['favicon.png','logos/linkedin.svg','logos/github.svg'];

    $: loading = false

    onMount(() => {
        loading = true;
    })
</script>

<!--
    DIV DE INICIO
-->
<div id="inicio">
    {#each preImgs as img}
        <link rel="preload" as="image" href={img} />
    {/each}
    
    {#if loading}
    <img src={preImgs[0]} alt="" transition:fade/> <!-- INSERTE FOTO PERSONAL -->
    <h1 transition:fade="{{ delay: 200 }}">Stefano Aguilera</h1>

    <div id="logos" transition:fade="{{ delay: 400 }}">
        <a href="https://www.linkedin.com/in/stefano-aguilera-293a40140/">
            <img id="llinkedin" src={preImgs[1]} alt="GitHub"/>
        </a>
        <a href="https://www.github.com/gothem">
            <img id="lgithub" src={preImgs[2]} alt="GitHub"/>
        </a>
    </div>

    <a id="shorcut" transition:fade="{{ delay: 600 }}" href="#proyectos">PROYECTOS</a>
    {/if}


</div>

<style>
    :global(body) {
        margin: 0;
        padding: 0;
        font-family: 'Noto Sans', sans-serif;
    }

    :global(a) {
        color:white;
        text-decoration-line: none;
    }

    :global(a:hover) {
        color:grey;
    }

    #inicio {
        display: grid;
        place-items: center;
        align-content: center;
        background-color: #131316;
        color: white;
        height: 100vh;
        width: 100vw;
    }
    
    #logos {
        padding-top: 10vh;
    }

    #llinkedin {
        height: 5em;
        padding-right: 2em;
    }

    #lgithub {
        height: 3.7em;
        padding-left: 2em;
        padding-right: 6em;
        padding-bottom: .65em;
    }

    #shorcut {
        padding-top: 20vh;
        font-size: large;
    }
</style>