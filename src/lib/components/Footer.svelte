<script>
  import TodoFilter from './TodoFilter.svelte';

  let itemsLeft = 0;
</script>

<footer class="footer">
  <span class="todo-count">{itemsLeft} items left</span>
  <TodoFilter />
  <button class="clear-completed" type="button">Clear completed</button>
</footer>
