<script>
  import Header from "./components/Header.svelte";
  import ShowPolls from "./components/ShowPolls.svelte";
  import AddPolls from "./components/AddPolls.svelte";

  let screen = "showPolls";
  let polls = [];

  function changeScreen(e) {
    screen = e.detail;
  }

  function addNewPoll(e) {
    polls = [e.detail, ...polls];
    screen = "showPolls"
  }
</script>

<Header />
<main>
  {#if screen == "showPolls"}
    <ShowPolls on:changeScreen={changeScreen}/>
  {:else if screen == "addPolls"}
    <AddPolls on:changeScreen={changeScreen} on:newPoll={addNewPoll}/>
    console.log("show")
  {/if}
</main>

<style>
</style>
