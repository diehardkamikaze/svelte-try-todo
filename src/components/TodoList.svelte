<script>
  // @ts-nocheck
  import TodoItem from "./TodoItem.svelte";

  let newTodo = "";
  let todos = [];

  const addTodoEnter = function (event) {
    if (event.code === "Enter") addTodo();
  };

  const addTodo = () => {
    if (newTodo) {
      todos.push(newTodo);
      todos = todos;
      newTodo = "";
    }
  };

  const deleteTodobyIndex = (event) => {
    todos.splice(event.detail, 1);
    todos = todos;
  };

  $: todosLenght = todos.length;
</script>

<main>
  <div class="tl">
    <h4>Всего дел {todosLenght}</h4>
    <label for="todo-input">Новое дело:</label>
    <input
      on:keydown={addTodoEnter}
      bind:value={newTodo}
      id="todo-inpup"
      type="text"
      name="todo-input"
      placeholder="Купить хлеба..."
    />
    <button on:click={addTodo}>Добавить</button>
    <ul class="list">
      {#each todos as todowka, i}
        <TodoItem on:delete={deleteTodobyIndex} {todowka} index={i} />
      {/each}
    </ul>
  </div>
</main>

<style>
  .tl {
    text-align: left;
    width: 450px;
    margin: auto;
  }

  .tl .list {
    list-style-type: none;
    border: 2px solid grey;
    border-radius: 5%;
    padding: 0;
    margin-top: 10px;
  }
</style>
