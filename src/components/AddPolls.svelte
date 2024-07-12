<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();

  let pollTitle = "";
  let titleValid = true;
  let pollOptions = ["", ""];
  let optionsValid = [true, true];
  let pollVotes = [0,0];
  let pollValid = false;

  function handleAddOptionClick() {
    pollOptions = [...pollOptions, ""];
    optionsValid.push(true);
    pollVotes.push(0)
  }

  function handleDeleteClick(index) {
    pollOptions.splice(index, 1);
    pollVotes.pop();
    pollOptions = pollOptions; 
  }

  function handleSubmit() {
    titleValid = pollTitle !== "";
    for (let i = 0; i < optionsValid.length; i++){
      optionsValid[i] = pollOptions[i] !== "";
    }
    if (titleValid && optionsValid.every((value) => {return value})){
      let newPoll = [pollTitle, ...pollOptions, ...pollVotes];
      dispatch("newPoll", newPoll)
    }
  }

  function changeScreenShowPolls() {
    dispatch("changeScreen", "showPolls")
  }
</script>

<form on:submit|preventDefault={handleSubmit}>
  <div class="fields">
    <div class="title field">
      <label for="title">Poll Title:</label>
      <input type="text" id="title" bind:value={pollTitle}>
      <p class="error" class:hide={titleValid}>title can't be empty</p>
    </div>
    <ul>
      {#each pollOptions as _, index}
        <div class="option field">
          <label for={`${index}`}>
            <p>Option:</p>
            {#if pollOptions.length > 2}
              <button class="delete" on:click={() => handleDeleteClick(index)}>Delete</button>
            {/if}
          </label>
          <input type="text" id={`${index}`} bind:value={pollOptions[index]}>
          <p class="error" class:hide={optionsValid[index]}>option can't be empty</p>
        </div>
      {/each}
      <button class="addOption" on:click={handleAddOptionClick} type="button">
        Add Option
      </button>
    </ul>
  </div>
  <button class="done add" type="submit">Add</button><button class="done cancel" type="button" on:click={changeScreenShowPolls}>Cancel</button>
</form>

<style>
  .fields {
    max-width: 600px;
    height: calc(var(--vh, 1vh) * 100 - 136px);
    padding: 0 20px;
    margin: 0 auto;
  }
  .field {
    display: flex;
    flex-direction: column;
    justify-content: left;
    padding: 8px 12px;
    margin: 10px;
    border: 2px dotted #292929;
    border-radius: 8px;
    line-height: 30px;
  }

  label {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .delete {
    color: #d91b42;
    background-color: transparent;
    text-align: center;
    font-size: 0.8rem;
  }
  input {
    padding: 8px 12px;
    border: none;
    border-radius: 5px;
    font-size: 1rem;
  }
  .error {
    padding: 2px 4px;
    color: #d91b42;
  }
  .hide {
    display: none;
  }
  .addOption {
    width: calc(100% - 20px);
    background-color: transparent;
    color: #808080;
    text-align: center;
    padding: 8px 12px;
    border: 2px dotted #292929;
    border-radius: 8px;
    margin: 10px;
    margin-bottom: 20px;
  }
  .done {
    width: 50%;
    padding: 12px;
    color: #ffffff;
    font-weight: bold;
  }
  .add {
    background-color: #45c496;
  }
  .cancel {
    background-color: #d91b42;
  }
</style>