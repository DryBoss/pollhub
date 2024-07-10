<script>
  let pollOptions = ["", ""];

  function handleAddOptionClick() {
    pollOptions = [...pollOptions, ""];
  }

  function handleDeleteClick(index) {
    pollOptions.splice(index, 1);
    pollOptions = pollOptions; 
  }

  function submit() {

  }
</script>

<form on:submit|preventDefault={submit}>
  <div class="fields">
    <div class="title field">
      <label for="title">Poll Title:</label>
      <input type="text" id="title">
    </div>
    <ul>
      {#each pollOptions as _, index}
        <div class="option field">
          <label for={`${index}`}>Option:</label>
          <input type="text" id={`${index}`}>
          {#if pollOptions.length > 2}
            <button class="delete" on:click={() => handleDeleteClick(index)}>Delete</button>
          {/if}
        </div>
      {/each}
      <button class="addOption" on:click={handleAddOptionClick}>
        Add Option
      </button>
    </ul>
  </div>
  <button class="done add">Add</button><button class="done cancel">Cancel</button>
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
  input {
    padding: 8px 12px;
    border: none;
    border-radius: 5px;
    font-size: 1rem;
  }
  .delete {
    width: 60px;
    color: #d91b42;
    background-color: transparent;
    text-align: center;
    font-size: 0.8rem;
    padding: 2px;
    margin-top: 8px;
    border: 2px solid #d91b42;
    border-radius: 5px;
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