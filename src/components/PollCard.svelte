<script>
  export let poll;
  let pollTitle = poll[0];
  let pollOptions = [];
  for (let i = 1; i < Math.floor(poll.length/2 + 1); i++) {
    pollOptions.push(poll[i])
  }
  let pollVoteCount = []
  for (let i = Math.floor(poll.length/2 + 1); i < poll.length; i++) {
    pollVoteCount.push(poll[i])
  }

</script>

<li>
  <p class="title">
    {pollTitle}
  </p>
  <ul class="options">
    {#each pollOptions as _, index}
      <li>
        <span>{pollOptions[index]}</span><span>{pollVoteCount[index]}</span>
      </li>
    {/each}
  </ul>
</li>

<style>
  .options li {
    display: flex;
    justify-content: space-between;
  }
</style>