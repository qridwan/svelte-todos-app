<script>
  import { createEventDispatcher } from "svelte";

  export let value;
  export let view;
  export let pin;
  const dispatch = createEventDispatcher();
  const select = (num) => () => (value += num);
  const clear = () => (value = "");
  const submit = () => dispatch("submit");
</script>

<h1 style="color: {pin ? '#333' : '#ccc'}">{view}</h1>
<div class="keypad">
  <button on:click={select(1)}>1</button>
  <button on:click={select(2)}>2</button>
  <button on:click={select(3)}>3</button>
  <button on:click={select("*")}>*</button>
  <button on:click={select(4)}>4</button>
  <button on:click={select(5)}>5</button>
  <button on:click={select(6)}>6</button>
  <button on:click={select("+")}>+</button>
  <button on:click={select(7)}>7</button>
  <button on:click={select(8)}>8</button>
  <button on:click={select(9)}>9</button>
  <button on:click={select("-")}>-</button>

  <button disabled={!value} on:click={clear}>clear</button>
  <button on:click={select(0)}>0</button>
  <button disabled={!value} on:click={submit}>submit</button>
  <button on:click={select("/")}>/</button>
</div>

<style>
  .keypad {
    display: grid;
    justify-content: center;
    grid-template-columns: repeat(4, 5em);
    grid-template-rows: repeat(4, 3em);
    grid-gap: 0.5em;
  }

  button {
    margin: 0;
    border-radius: 5px;
    cursor: pointer;
  }
</style>
