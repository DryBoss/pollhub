<script>
  import Header from "./components/Header.svelte";
  import ShowPolls from "./components/ShowPolls.svelte";
  import AddPolls from "./components/AddPolls.svelte";

  let screen = "addPolls";
  let polls = [];

  function addNewPoll(e) {
    polls = [...polls, e.detail];
    screen = "showPolls"
  }
</script>

<Header />
<main>
  {#if screen == "showPolls"}
    <ShowPolls />
  {:else if screen == "addPolls"}
    <AddPolls on:newPoll={addNewPoll}/>
    console.log("show")
  {/if}
</main>

<style>
</style>
