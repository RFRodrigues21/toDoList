<script>
    import TodoForm from "../components/TodoForm.svelte";
    import Todo from "../components/Todo.svelte";
    import { todos } from "../stores/todoStore"
</script>

<main>
    <h1 class="text-2xl font-bold text-center text-gray-800 md:text-3xl">My Todos</h1>
    <TodoForm></TodoForm>
    {#each $todos as todo}
      <Todo todo={todo} index={todo.id}/>
    {/each}
</main>