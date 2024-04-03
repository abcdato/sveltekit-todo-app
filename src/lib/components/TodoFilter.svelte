<script>
  import { todos, filteredTodos } from '../stores/store';

  let filters = ['all', 'active', 'completed'];

  $: selectedFilter = 'all';
  $: $filteredTodos = filterTodos($todos, selectedFilter);

  function filterTodos($todos, filter) {
    switch (filter) {
      case 'all':
        return $todos;
      case 'active':
        return $todos.filter((todo) => !todo.completed);
      case 'completed':
        return $todos.filter((todo) => todo.completed);
    }
  }
</script>

<ul class="filters">
  {#each filters as filter}
    <li>
      <button
        on:click={() => (selectedFilter = filter)}
        class:selected={selectedFilter === filter}
        type="button">{filter}</button
      >
    </li>
  {/each}
</ul>
