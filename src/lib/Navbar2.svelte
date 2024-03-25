<script>
    import { onMount } from "svelte";

    export let data;
    let windowWidth;
    let clicked = false;

    onMount(() => {
        windowWidth = window.innerWidth;
        window.addEventListener("resize", handleResize);
    });

    function handleResize() {
        windowWidth = window.innerWidth;
        if (windowWidth >= 1024) {
            clicked = false;
        }
    }

    const handleClick = () => {
        clicked = !clicked;
    };
    const resetCollaps = () => {
        clicked = false;
    };
</script>

<nav class={clicked ? "navbar-clicked" : "navbar"}>
    <div class="navItemsContainer">
        {#if data.logoLink}
            <a class="logo-link-text" href={data.linkUrl}>
                <img
                    class="logo"
                    src={data.logoSrc}
                    alt={data.logoAlt}
                />{data.optionalLinkText ? data.optionalLinkText : ""}</a
            >
        {:else}
            <img class="logo" src={data.logoSrc} alt={data.logoAlt} />
        {/if}
        <div class="nowf">
            {#each data.links as link}
                <div
                    class={clicked ? "navbar-item-clicked" : "navbar-item"}
                    on:click={resetCollaps}
                    on:keypress={resetCollaps}
                    role="button"
                    tabindex="0"
                >
                    <a class="link-text" href={link.url}>{link.linkText}</a>
                </div>
            {/each}
        </div>
    </div>
</nav>

<style>
    .nowf {
        width: 40%;
        display: flex;
        justify-content: space-around;
    }
    button {
        background-color: rgb(255, 255, 255, 0);
    }
    .logo {
        width: 40px;
    }
    .navItemsContainer {
        width: 100%;
        display: flex;
        justify-content: space-around;
    }
    .navbar {
        top: 0;
        width: 100%;
        height: 3rem;

        color: #fff;
        z-index: 999;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        align-items: center;
        transition: all 0.2s ease-out;
    }
    .navbar-clicked {
        position: fixed;
        top: 0;
        width: 100%;
        background-color: black;
        color: #0e0d0d;
        z-index: 999;

        justify-content: space-around;
        align-items: center;
        transition: all 0.2s ease-out;
        height: 4em;
    }

    .navbar-item {
        display: flex;
        height: 2em;
        color: #fff;
        font-size: 1.2em;
        align-items: center;
    }
    .navbar-item:hover {
        border-bottom: 2px solid #ffffff;
        transition: all 0.2s ease-out;
    }
    .navbar-item-clicked {
        display: flex;
        height: 4em;
        color: #fff;
        font-size: 1.2em;
        align-items: center;
    }
    .navbar-item-clicked:hover {
        color: #fff;
        border-bottom: 4px solid #fff;
        transition: all 0.2s ease-out;
    }
    .icon-wrapper {
        margin-right: 1em;
    }
    .menu-icon {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }
    .fa-bars {
        display: flex;
        font-size: 2rem;
        cursor: pointer;
    }
    .fa-times {
        display: flex;
        font-size: 2rem;
        cursor: pointer;
    }
    .fa-times:hover {
        position: relative;
        box-shadow: 0 0 20px 5px #777575;
        background-color: rgba(119, 117, 117, 0.58);
        transition: all 0.2s ease-out;
        border-radius: 50%;
    }
    .fa-bars:hover {
        position: relative;
        box-shadow: 0 0 20px 5px#777575;
        background-color: rgba(119, 117, 117, 0.58);
        transition: all 0.2s ease-out;
        border-radius: 50%;
    }
    @media (max-width: 1024px) {
        /* CSS styles for tablets/mobile go here */
        button:hover {
            background-color: rgb(255, 255, 255, 0);
        }
        button:focus {
            background-color: #fff;
            color: #242424;
            transition: all 0.2s ease-out;
        }

        a:focus {
            color: #242424;
            background-color: #fff;
            color: #242424;
            transition: all 0.2s ease-out;
        }
        .navbar {
            height: 4.5em;
            width: 100vw;
            color: #fff;
            z-index: 999;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
        }
        .navbar-clicked {
            height: 100vh;
            width: 100vw;
            color: #fff;
            z-index: 999;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
        }
        .navbar-item {
            display: none;
        }
        .navbar-item-clicked {
            display: flex;
            width: 100vw;
            color: #fff;
            font-size: 1.2em;
            align-items: center;
            justify-content: center;
        }
        .navbar-item-clicked:hover {
            background-color: #fff;
            color: #242424;
            transition: all 0.2s ease-out;
        }
        .navbar-item-clicked:hover a {
            color: #242424;
        }
        .navbar-item:hover a {
            color: #242424;
        }
        .navbar-item:hover {
            background-color: #fff;
            color: #242424;
            transition: all 0.2s ease-out;
        }
        .link-text {
            display: flex;
            width: 100%;
            height: 100%;
            align-items: center;
            justify-content: center;
        }

        .link-text:hover {
            color: #242424;
        }
        .menu-icon {
            width: 100%;
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: center;
            height: 3em;
            padding-top: 1em;
            padding-bottom: 0.5em;
        }
        .fa:hover {
            color: #242424;
        }
    }

    @media (max-width: 768px) {
        /* CSS styles for mobile phones go here */
    }
    :global(body) {
        background-color: rgb(147, 147, 255);
    }
</style>
