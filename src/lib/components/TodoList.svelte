<script>
  import { todos, filteredTodos } from '../stores/store';
  import Todo from './Todo.svelte';
</script>

{#if $todos.length > 0}
  <main class="main">
    <ul class="todo-list">
      {#each $filteredTodos as todo}
        <Todo {todo} />
      {/each}
    </ul>
  </main>
{/if}
