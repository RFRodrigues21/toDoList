
<!-- Place the following <script> and <textarea> tags your HTML's <body> -->

<script>
    import {addTodo } from "../stores/todoStore"
    import { Textarea, Label, MultiSelect, Badge } from 'flowbite-svelte';
    import DatePicker from '../components/DatePicker.svelte';
    let selectedLabels = [];
    let labels = [
        { value: 'lb1', name: 'Label 1', color: 'indigo' },
        { value: 'lb2', name: 'Label 2', color: 'green' },
        { value: 'lb3', name: 'Label 3', color: 'blue' },
        { value: 'lb4', name: 'Label 4', color: 'red' },
        { value: 'lb5', name: 'Label 5', color: 'yellow' }
    ];

    let title = '';
    let text = '';
    

    const handleSubmit = () => {
        addTodo(title, text, selectedLabels);
        title = '';
        text = '';
        console.log(selectedLabels);
    }

</script>

<form action="" class="my-6" on:submit|preventDefault={handleSubmit}>
    <div class="flex flex-col text-sm mb-2">
        <label for="todo" class="font-bold mb-2 text-gray-800">Todo</label>
        <input type="text" bind:value={title} name="todo" placeholder="Watcha gotta do?" class="appearance-non shadow-sm border border-gray-200 p-2 focus:outline-none focus:border-gray-500 rounded-lg mb-2">
        <Label for="textarea-id" class="font-bold mb-2 text-gray-800">Your message</Label>
        <Textarea id="textarea-id" placeholder="Your message" rows="4" name="message" bind:value={text} class="mb-2"/>
        <!--<div class="mt-2">
            <DatePicker ></DatePicker>
        </div> -->
        <Label for="labels" class="font-bold mb-2 text-gray-800">Labels</Label>
        <MultiSelect items={labels} bind:value={selectedLabels} size="lg" id="labels" let:item let:clear>
            <Badge color={item.color} dismissable params={{ duration: 100 }} on:close={clear}>
            {item.name}
          </Badge></MultiSelect>

    </div>
    <button type="submit" class="w-full shadow-sm rounded bg-blue-500 hover:bg-blue-600 text-white py-2 px-4">Submit</button>
</form>

<svelte:head>
	<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">
</svelte:head>
