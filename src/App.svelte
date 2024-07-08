<script>
  import Header from "./components/Header.svelte";
  import Footer from "./components/Footer.svelte";
</script>

<Header />
<main></main>
<Footer />

<style>
  main {
    min-height: calc(100vh - 155px);
    min-height: calc(var(--vh, 1vh) * 100 - 155px);
  }
</style>
