<script>
    import Navbar from "$lib/Navbar.svelte";
    import { fade } from "svelte/transition";
    import { onMount } from "svelte";
    let loadHighQuality = false;

    onMount(() => {
        loadHighQuality = true;
    });
</script>

<div class="pageFull">
    <Navbar />
    {#if loadHighQuality}
        <div
            class="backgroundHighQuality -z-10"
            in:fade={{ duration: 300 }}
        ></div>
    {/if}
    <div class="backgroundLowQuality -z-20"></div>
</div>

<style>
    .pageFull {
        height: 100vh;
        position: relative;
    }
    .backgroundLowQuality,
    .backgroundHighQuality {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-size: cover;
        background-repeat: no-repeat;
    }
    .backgroundLowQuality {
        background-image: url("/images-ass-quali/hero-gallery.jpg");
    }

    .backgroundHighQuality {
        background-image: url("/hero/hero-gallery.jpg");
    }
</style>
