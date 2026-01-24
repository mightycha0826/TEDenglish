<script>
    import Header from "$lib/assets/components/Header.svelte";
    import Footer from "$lib/assets/components/Footer.svelte";
    import "./layout.css";
</script>

<svelte:head>
    <title>TED잉글리시</title>
</svelte:head>

<Header />
<main>
    <slot />
</main>
<Footer />
