<script>
  export let todoItem;
  export let deleteItem;
  export let DoneTask;
</script>

<div class="todo-item">
  <span>{todoItem.text}</span>
  <div class="buttons">
    <button class="deleteButton" on:click={deleteItem(todoItem.id)}
      >Delete</button
    >
    <button class="Done" on:click={DoneTask(todoItem.id)}>Done</button>
  </div>
</div>

<style>
  .todo-item span {
    align-self: center;
  }
  .Done {
    background-color: #69ea7c;
    color: white;
  }
  .deleteButton {
    background-color: #ff3e00;
    color: white;
  }
  .todo-item {
    width: 500px;
    border: 1px solid black;
    border-radius: 2px;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
    padding: 1em;
    margin: 0 0 1em 0;
    margin-top: 10px;
    align-self: center;
    text-align: left;
    display: flex;
    justify-content: space-between;
  }
</style>
