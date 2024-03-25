<script>
    import Navbar from "$lib/Navbar.svelte";
</script>

<div class="pageFull bg-slate-500">
    <Navbar />
</div>

<style>
    .pageFull {
        height: 100vh;
        background-image: url("/hero/hero-about.jpg");
        background-size: cover;
        background-repeat: no-repeat;
    }
</style>
