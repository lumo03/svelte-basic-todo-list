<script lang="ts">
  type ToDo = {
    name: string;
    done: boolean;
  }

  let todos: ToDo[] = [];
  let todoName = "";

  function addToDo(name: string) {
    if (name.trim() === "") return;
    todos = [...todos, { name, done: false }];
    console.log(todos);
  }
</script>

<main>
  <h1>ToDos:</h1>
  {#if todos.length === 0}
    <p>There are no ToDos yet.</p>
  {:else}
    <ul>
      {#each todos as todo}
        <li on:click={() => todo.done = !todo.done} class:done={todo.done}>
          {todo.name}
        </li>
      {/each}
    </ul>
  {/if}
  <div>
    <input bind:value={todoName}>
    <button on:click={() => addToDo(todoName)}>Add</button>
  </div>
</main>

<style>
  .done {
    text-decoration: line-through;
  }
</style>
