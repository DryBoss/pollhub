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

<li class="poll">
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
  .poll {
    width: 900px;
    padding: 20px;
    margin: 20px ;
    border: 2px dashed #ffa31a;
    border-radius: 10px;
  }
  .title {
    padding: 20px;
  }
  ul {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
    width: 100%;
    padding: 10px;
  }
  .options li {
    display: flex;
    justify-content: space-between;
    padding: 10px 20px;
    background-color: #292929;
    border-radius: 20px;
  }
  .options li:hover {
    opacity: 0.5;
  }
</style>