<script lang="ts">
  type ToDo = {
    name: string;
    done: boolean;
  }

  let todos = <ToDo[]>[];
  let todoName = ""

  function addToDo(name: string) {
    if (name.trim() === "") return;
    todos = [...todos, {
      name,
      done: false
    } as ToDo]
    console.log(todos);
  }
</script>

<main>
  <h1>ToDos:</h1>
  {#if todos.length < 1}
  <p>Es gibt noch keine ToDos.</p>
  {:else}
  {#each todos as todo}
    <div on:click={() => todo.done = !todo.done} class:done={todo.done}>{todo.name}</div>
  {/each}
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