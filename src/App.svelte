<script>
    import NavBar from "./components/navBar.svelte";
    import Blog from "./components/blog.svelte";
</script>

<NavBar />

<section>
    <Blog />
    <Blog />
</section>


<style>
    section {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: .5rem;
        padding: .5rem;
    }
</style>