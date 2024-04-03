<script>
  export let todo;
</script>

<li class:editing={todo.editing} class:completed={todo.completed}>
  <div class="view">
    <input class="toggle" type="checkbox" checked={todo.completed} />
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
