<script>
  import Todo from "./Todo.svelte";
  let todo = "TodoList";
  let todoList = [
    { id: Date.now(), text: "Take the trash out", Done: false },
    { id: Date.now() + 1, text: "Study", Done: false },
  ];
</script>

<main>
  <h2>Svelte {todo}!</h2>
  <Todo {todoList} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h2 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
