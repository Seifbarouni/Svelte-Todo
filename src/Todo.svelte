<script>
  export let todoList;
  let DoneTasks = [];
  let showDoneTasks = false;
  let item;
  function AddTodo() {
    if (item) {
      todoList = [...todoList, { id: Date.now(), text: item, Done: false }];
      item = undefined;
    }
  }
  function deleteItem(id) {
    todoList = todoList.filter((item) => item.id !== id);
  }
  function DoneTask(id) {
    let todo = todoList.find((t) => t.id === id);
    todo.Done = true;
    DoneTasks = [...DoneTasks, todo];
    todoList = todoList.filter((item) => item.id !== id);
  }
  function showDone() {
    showDoneTasks = true;
  }
  function hideDone() {
    showDoneTasks = false;
  }
</script>

<br />
<input name="newTodo" type="text" bind:value={item} placeholder=" New Todo" />
<button on:click={AddTodo} class="AddButton">Add</button>
{#if showDoneTasks === false}
  <button class="SeeButton" on:click={showDone}>See finished tasks</button>
{:else}
  <button class="deleteButton" on:click={hideDone}>Hide finished tasks</button>
{/if}

{#if item}
  <p>Your New task : {item}</p>
{/if}
<div class="todos">
  {#each todoList as todoItem}
    <div class="todo-item">
      <span>{todoItem.text}</span>
      <div class="buttons">
        <button class="deleteButton" on:click={deleteItem(todoItem.id)}
          >Delete</button
        >
        <button class="Done" on:click={DoneTask(todoItem.id)}>Done</button>
      </div>
    </div>
  {/each}
</div>
{#if showDoneTasks === true}
  <div class="finished">
    {#if DoneTasks.length === 0}
      <hr />
      <p>Go Do your tasks!</p>
    {:else}
      <hr />
      {#if todoList.length === 0}
        <p>Congratulations! you have achieved all your tasks for today!</p>
      {:else}
        <p>Done:</p>
      {/if}
      {#each DoneTasks as task}
        <div class="todo-item">{task.text}</div>
      {/each}
    {/if}
  </div>
{/if}

<style>
  .todo-item {
    width: 500px;
    border: 1px solid #aaa;
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
  hr {
    width: 500px;
  }
  .todo-item span {
    align-self: center;
  }
  .todos {
    display: flex;
    flex-direction: column;
    align-content: center;
  }
  .deleteButton {
    background-color: #ff3e00;
    color: white;
  }
  .Done {
    background-color: #69ea7c;
    color: white;
  }
  .AddButton {
    background-color: #369ef9;
    color: white;
  }
  .finished {
    display: flex;
    flex-direction: column;
  }
  .SeeButton {
    background-color: #d3d34c;
    color: white;
  }
</style>
