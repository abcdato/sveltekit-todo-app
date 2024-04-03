<script>
  import { v4 as uuidv4 } from 'uuid';
  import { todos } from '../stores/store';

  function createTodo(text) {
    return {
      id: uuidv4(),
      title: text,
      completed: false,
      editing: false,
    };
  }

  function addTodo(todo) {
    const newTodo = createTodo(todo);
    $todos = [...$todos, newTodo];
  }

  let todo = '';
  function handleSubmit() {
    if (todo.trim() === '') {
      todo = '';
      return;
    }
    addTodo(todo.trim());
    todo = '';
  }
</script>

<form class="new-todo-form" on:submit|preventDefault={handleSubmit}>
  <input
    bind:value={todo}
    class="new-todo"
    placeholder="What needs to be done?"
    type="text"
    name="label"
  />
  <input class="visually-hidden" type="submit" value="Submit" />
</form>
