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
    <ul class="pollList-1">
      {#each polls as poll, index (index)}
        {#if index%2 === 0}
          <PollCard {poll}/>
        {/if}
      {/each}
    </ul>
    <ul class="pollList-2">
      {#each polls as poll, index (index)}
        {#if index%2 === 1}
          <PollCard {poll}/>
        {/if}
      {/each}
    </ul>
  </div>
  <button class="createPoll" on:click={changeScreenAddPolls}>Create poll</button>
</div>

<style>
  .pollList {
    display: flex;
    max-width: 900px;
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