<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();

  function changeScreenAddPolls() {
    dispatch("changeScreen", "addPolls")
  }
</script>

<div class="addPoll">
  <ul class="pollList">
    
  </ul>
  <button class="createPoll" on:click={changeScreenAddPolls}>Create poll</button>
</div>

<style>
  .pollList {
    max-width: 600px;
    height: calc(var(--vh, 1vh) * 100 - 136px);
    padding: 0 20px;
    margin: 0 auto;
  }
  .createPoll {
    width: 100%;
    padding: 12px;
    color: #1b1b1b;
    font-weight: bold;
    background-color: #ffa31a;
  }
</style>