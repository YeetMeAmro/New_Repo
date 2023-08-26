<script>
    import SideBar from "./sideBar.svelte";

    let menuOpen = false;

    $: document.body.onscroll = closeMenu
    $: document.body.addEventListener("keydown", (event) => {
        if (event.key == "Escape") {
            menuOpen = false
        }
    })

    function openMenu() {
        menuOpen = !menuOpen;
    }

    function closeMenu() {
        menuOpen = false;
    }

</script>

<section class="block-container">
    <section class="item-container">
        <nav class="nav-items image logo"><img src="../public/vite.svg" alt=""></nav>
        <nav class="nav-items links">
            <a href="./">Home</a>
            <a href="./">Products</a>
            <a href="./">Pricing</a>
        </nav>
        <nav class="nav-items image menu" on:click={openMenu}>
            <img src="../public/Menu.svg" alt="">
        </nav>
    </section>
</section>

{#if menuOpen}
    <div on:click={closeMenu}>
    </div>
    <SideBar />
{/if}

<style>
    div {
        position: fixed;
        top: 3rem;
        right: 0;
        height: calc(100vh - 3rem);
        width: 100vw;
        background-color: #2a2c2055;
    }
    .block-container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 3rem;
        padding: 0 .5rem;
        background-color: #2a2c20;
    }
    .item-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: min(100%, 768px);
    }
    .image {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 2.5rem;
        width: 2.5rem;
        border-radius: .5rem;
    }
    .image img {
        user-select: none;
        height: 2rem;
        width: 2rem;
    }
    .links {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 1rem;
    }
    .links a {
        user-select: none;
        color: #bebebe;
        text-decoration: none;
        text-transform: uppercase;
        padding: .5rem;
        border-radius: .5rem;
    }
    .links a:active, .image:active {
        color: rgb(123, 29, 255);
        background-color: #bebebeeb;
    }

    @media (width <= 415px) {
        .links {
            display: none;
        }
    }
    @media (width > 415px) {
        .menu {
            display: none;
        }
    }
</style>