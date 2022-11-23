<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let todowka = "";
  export let index = "";

  const deleteTodoItem = () => {
    dispatch("delete", index);
  };
</script>

<li>
  <span>{index + 1}: {todowka}</span><a href="#" on:click={deleteTodoItem}
    >Delete</a
  >
</li>

<style>
  li {
    display: flex;
    justify-content: space-between;
    padding: 5px;
    font-weight: bold;
    font-size: 18px;
    background-color: slateblue;
    color: white;
  }

  li a {
    color: white;
  }
</style>
