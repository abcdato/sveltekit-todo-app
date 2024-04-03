<script>
  import TodoFilter from './TodoFilter.svelte';
  import { todos } from '../stores/store';

  $: itemsLeft = $todos.filter((todo) => !todo.completed).length;

  const clearCompleted = () => {
    const incompletedTodos = $todos.filter((todo) => !todo.completed);
    $todos = [...incompletedTodos];
  };
</script>

<footer class="footer">
  <span class="todo-count">
    {itemsLeft}
    {itemsLeft === 1 ? 'item' : 'items'} left
  </span>
  <TodoFilter />
  <button on:click={clearCompleted} class="clear-completed" type="button">Clear completed</button>
</footer>
