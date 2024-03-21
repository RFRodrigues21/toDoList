<script>
    import TodoForm from "../components/TodoForm.svelte";
    import Todo from "../components/Todo.svelte";
    import { todos } from "../stores/todoStore"
    import {Avatar, Button } from 'flowbite-svelte';

    let showForm = false;
</script>

<main>
  <div class="flex justify-center space-x-4 rtl:space-x-reverse">
    <h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">My Todos</h1>
    <Avatar href="%sveltekit.assets%/todoIcon.png" />
    <div class="justify-self-end">
      <Button on:click={() => showForm = !showForm}>
        {showForm ? "Close Form" : "New Post"}
      </Button>
    </div>
  </div>

  {#if showForm}
    <TodoForm id="form" />
  {/if}
  
  {#each $todos as todo}
    <div class="mb-2 mt-10">
      <Todo todo={todo} index={todo.id} />
    </div>
  {/each}
</main>