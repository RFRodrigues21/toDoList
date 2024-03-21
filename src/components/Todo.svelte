<!--<script>
    export let todo;
    import {deleteTodo, toggleTodoCompleted} from '../stores/todoStore.js';
    
</script>


<li class="bg-white flex items-center shadow-sm border border-gray-200 rounded-lg my-2 py-2 px-4">
    <input
        name="completed"
        type="checkbox"
        checked={todo.completed}
        on:change={() => toggleTodoCompleted(todo.id)}
        class="mr-2 form-checkbox h-5 w-5"
    />
    <span
        class={`flex-1 text-gray-800  ${
            todo.completed ? 'line-through' : ''
        }`}
    >
        {todo.text}
    </span>
    <button
        type="button"
        class="text-sm bg-red-500 hover:bg-red-600 text-white py-1 px-2 rounded focus:outline-none focus:shadow-outline"
        on:click={() => deleteTodo(todo.id)}
    >
        Delete
    </button>
</li>-->

<script>
    export let todo;
    import { Card, Button,Badge } from 'flowbite-svelte';
    import { CloseOutline  } from 'flowbite-svelte-icons';
    import {deleteTodo, toggleTodoCompleted} from '../stores/todoStore.js';

    let labels = [
        { value: 'lb1', name: 'Label 1', color: 'indigo' },
        { value: 'lb2', name: 'Label 2', color: 'green' },
        { value: 'lb3', name: 'Label 3', color: 'blue' },
        { value: 'lb4', name: 'Label 4', color: 'red' },
        { value: 'lb5', name: 'Label 5', color: 'yellow' }
    ];

    function getColorByLabelValue(labelValue) {
        for (let i = 0; i < labels.length; i++) {
            if (labels[i].value === labelValue) {
                return labels[i].color;
            }
        }
    }

    function getNameByLabelValue(labelValue) {
        for (let i = 0; i < labels.length; i++) {
            if (labels[i].value === labelValue) {
                return labels[i].name;
            }
        }
    }
    
  </script>
  
  <Card >
    <div class="space-x-2 mb-2">
        {#each todo.selectedLabels as label}
            <Badge color='{getColorByLabelValue(label)}'>{getNameByLabelValue(label)}</Badge>
        {/each}
    </div>
    <div class="flex flex-row justify-between">
        <h5 class={`mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white ${todo.completed ? 'line-through' : ''} `}>{todo.title}</h5>
        <input
            name="completed"
            type="checkbox"
            checked={todo.completed}
            on:change={() => toggleTodoCompleted(todo.id)}
            class="mr-2 form-checkbox h-5 w-5"
        />
    </div>
    <p class="mb-3 font-normal text-gray-700 dark:text-gray-400 leading-tight">{todo.text}</p>
    <Button class="w-fit" on:click={() => deleteTodo(todo.id)}>
      Delete <CloseOutline  class="w-3.5 h-3.5 ms-2 text-white" />
    </Button>
  </Card>