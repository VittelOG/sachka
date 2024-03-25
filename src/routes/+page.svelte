<script>
    import Navbar from "$lib/Navbar.svelte";
</script>

<div class="pageFull">
    <Navbar />
    <div class="textContain">
        <h1 class="textLead text-slate-50">
            Are you ready to experience shaolin life?
        </h1>
    </div>
</div>

<style>
    .pageFull {
        height: 100vh;
        background-image: url("/hero/hero-back.png");
        background-size: cover;
        background-repeat: no-repeat;
    }
    .textContain {
        display: flex;
        justify-content: start;
        align-items: end;
        height: 100vh;
        padding-bottom: 30vh;
        font-size: 5.5vw;
    }
</style>
