<script>
    import { onMount } from "svelte";
    import { cubicOut } from "svelte/easing";
    import { slide } from "svelte/transition";

    import { fade } from "svelte/transition";

    let clicked = false;
    let windowWidth;
    let isNarrowScreen;
    let myDur = 400;
    let myAx = "x";
    let myDel = 150;
    let delInc = 30;

    onMount(() => {
        if (typeof window !== "undefined") {
            windowWidth = window.innerWidth;
            isNarrowScreen = window.innerWidth <= 768;

            window.addEventListener("resize", handleResize);
        }
    });
    function handleResize() {
        if (typeof window !== "undefined") {
            windowWidth = window.innerWidth;
            isNarrowScreen = window.innerWidth <= 768;
            if (windowWidth >= 1024) {
                clicked = false;
            }
        }
    }
    const handleClick = () => {
        clicked = !clicked;
    };
    const resetCollaps = () => {
        clicked = false;
    };
</script>

{#if !isNarrowScreen}
    <nav class={clicked ? "navbar-clicked" : "navbar"}>
        <div class="logo">
            <a href="./">
                <img class="nav-logo w-26" src="vector-logo-w.svg" alt="logo" />
            </a>
        </div>
        <div class="container text-slate-200">
            <a href="about">About</a>
            <a href="trainer">Trainer</a>
            <a href="retreats">Retreats</a>
            <a href="gallery">Gallery</a>
            <a href="faq">FAQ</a>
            <a href="registration">Registration</a>
            <a href="contact">Contact</a>
        </div>
    </nav>
{:else}
    <nav class={clicked ? "navbar-clicked" : "navbar"}>
        <div class="logo">
            <img class="nav-logo w-26" src="vector-logo-w.svg" alt="logo" />
        </div>
        <div class="container text-slate-200">
            {#if clicked}
                <button
                    on:click={handleClick}
                    class="text-slate-100 close-button pt-2"
                    out:fade={{ delay: 0, duration: 300 }}
                    in:fade={{ delay: 250, duration: 300 }}>X</button
                >
                <div
                    class="text-slate-200 text-2xl clicked-container {clicked
                        ? 'active'
                        : ''}"
                    transition:slide={{
                        axis: "y",
                        duration: myDur,
                        easing: cubicOut,
                    }}
                >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="about">About</a
                    >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="trainer">Trainer</a
                    >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel + delInc,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="retreats">Retreats</a
                    >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel + delInc * 2,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="gallery">Gallery</a
                    >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel + delInc * 3,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="faq">Faq</a
                    >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel + delInc * 4,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="registration">Registration</a
                    >
                    <a
                        in:slide={{
                            axis: myAx,
                            delay: myDel + delInc * 5,
                            duration: myDur,
                        }}
                        out:fade={{ delay: 0, duration: 200 }}
                        href="contact">Contact</a
                    >
                </div>
            {/if}
            <button
                on:click={handleClick}
                class="text-slate-200 hover:text-white"
            >
                <svg
                    class="w-6 h-6"
                    fill="none"
                    stroke="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M4 6h16M4 12h16m-7 6h7"
                    ></path>
                </svg>
            </button>
        </div>
    </nav>
{/if}

<style>
    .navbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-left: 0.5rem;
        height: 4.5rem;
    }
    .close-button {
        position: absolute;
        top: 10px;
        right: 35px;
        background: none;
        border: none;
        /* Change this to your preferred color */
        font-size: 1.5em; /* Change this to your preferred size */
        cursor: pointer;
        z-index: 1000;
    }
    .close-button:hover {
        color: #fff; /* Change this to your preferred hover color */
    }
    .navbar-clicked {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0.5rem;
    }
    .container {
        display: flex;
        justify-content: flex-end;
        width: 100vw;
    }
    .container a {
        margin-left: 1rem;
    }
    .container a:hover {
        color: #fff; /* Change this to your preferred hover color */
    }
    .clicked-container {
        background-color: #221f1f; /* Change this to your preferred dark color */
        /* Change this to your preferred text color */
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh; /* This will make it span the full height of the viewport */
        width: 100vw; /* Adjust this to your preference */
        display: flex;
        flex-direction: column;
        padding: 20px;
    }
    .clicked-container a {
        color: inherit; /* Makes the links the same color as the text in the container */
        text-decoration: none; /* Removes the underline from the links */
        margin-top: 1rem;
        width: 11rem;
        font-family: "Inter-SemiBold", sans-serif;
    }
    .clicked-container a:hover {
        color: #fff; /* Change this to your preferred hover color */
    }
</style>
