<script>
// @ts-nocheck

  import PollCard from "./PollCard.svelte";

  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();

  export let polls;

  function changeScreenAddPolls() {
    dispatch("changeScreen", "addPolls")
  }
</script>

<div class="addPoll">
  <div class="pollList">
    <ul>
      {#each polls as poll, index (index)}
          <PollCard {poll}/>
      {/each}
    </ul>
  </div>
  <button class="createPoll" on:click={changeScreenAddPolls}>Create poll</button>
</div>

<style>
  .pollList {
    width: 100%;
    height: calc(var(--vh, 1vh) * 100 - 136px);
  }
  ul {
    width: 100%;
    display: grid;
    justify-content: center;
  }
  .createPoll {
    width: 100%;
    padding: 12px;
    color: #1b1b1b;
    font-weight: bold;
    background-color: #ffa31a;
  }
</style>