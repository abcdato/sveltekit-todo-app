<script>
  import { todos } from '../stores/store';

  export let todo;

  function toggleProp(arr, id, propName) {
    return arr.map((el) => {
      if (el.id === id) {
        return { ...el, [propName]: !el[propName] };
      }
      return el;
    });
  }

  function removeTodo() {
    const filteredTodos = $todos.filter((item) => item.id !== todo.id);
    $todos = [...filteredTodos];
  }

  function handleComplete() {
    $todos = toggleProp($todos, todo.id, 'completed');
  }

  function handleSubmit() {
    if (todo.title.trim() === '') {
      removeTodo();
      return;
    }
    handleEdit();
  }

  function handleEdit() {
    $todos = toggleProp($todos, todo.id, 'editing');
  }
</script>

<li class:editing={todo.editing} class:completed={todo.completed}>
  <div class="view">
    <input on:click={handleComplete} class="toggle" type="checkbox" checked={todo.completed} />
    <label for="">
      <span class="title">{todo.title}</span>
    </label>
    <button on:click={handleEdit} class="icon icon-edit" type="button" aria-label="edit" />
    <button on:click={removeTodo} class="icon icon-destroy" type="button" aria-label="delete" />
  </div>
  <form on:submit|preventDefault={handleSubmit}>
    <input bind:value={todo.title} type="text" class="edit" />
  </form>
</li>
