<script>
  let pollOptions = ["option1", "option2"];

  function handleAddOptionClick() {
    pollOptions = [...pollOptions, `option${pollOptions.length + 1}`];
  }
</script>

<form>
  <div class="fields">
    <div class="title field">
      <label for="title">Poll Title</label>
      <input type="text" id="title">
    </div>
    <ul>
      {#each pollOptions as option, index}
        <div class="option field">
          <label for={option}>Option {index + 1}</label>
          <input type="text" id={option}>
        </div>
      {/each}
      <div class="addOption" on:click={handleAddOptionClick}>
        Add Option
      </div>
    </ul>
  </div>
  <button class="add">Add</button><button class="cancel">Cancel</button>
</form>

<style>
  .fields {
    min-height: calc(var(--vh, 1vh) * 100 - 136px);
    padding: 0 20px;
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
  }
  .addOption {
    color: #808080;
    text-align: center;
    padding: 8px 12px;
    border: 2px dotted #292929;
    border-radius: 8px;
    margin: 10px;
    margin-bottom: 20px;
  }
  button {
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