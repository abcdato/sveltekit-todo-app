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

  function handleComplete() {
    $todos = toggleProp($todos, todo.id, 'completed');
  }
</script>

<li class:editing={todo.editing} class:completed={todo.completed}>
  <div class="view">
    <input on:click={handleComplete} class="toggle" type="checkbox" checked={todo.completed} />
    <label for="">
      <span class="title">{todo.title}</span>
    </label>
    <button class="icon icon-edit" type="button" aria-label="edit" />
    <button class="icon icon-destroy" type="button" aria-label="delete" />
  </div>
  <form>
    <input type="text" class="edit" />
  </form>
</li>
