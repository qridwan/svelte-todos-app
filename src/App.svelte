<script>
  export let name;
  import Calculator from "./components/Calculator.svelte";
  import Nested from "./components/Nested.svelte";
  import Todo from "./components/Todo.svelte";
  import Login from "./routes/Login.svelte";
  function handleMessage(event) {
    console.log("event: ", event);
    alert(event.detail.text);
  }

  let pin;
  function handleSubmit(e) {
    console.log("event: ", pin);
    let minFunction = pin.split("-");
    let plusFunction = pin.split("+");
    let devideFunction = pin.split("/");
    let multiplyFunction = pin.split("*");
    if (minFunction.length > 1) {
      pin = Number(minFunction[0]) - Number(plusFunction[1]);
      console.log(
        "view: ",
        pin,
        Number(minFunction[0]) - Number(minFunction[1]),
        minFunction
      );
    }
  }
  $: view = pin ? pin : "enter your pin";
  let page = document.location.hash;
  window.onpopstate = function (event) {
    page = document.location.hash;
  };
</script>

<main>
  <h1>Welcome Back {name}!</h1>
  <!-- <Nested on:message={handleMessage} /> -->
  {#if page === "#login"}
  <a href="/">Home</a>
  {:else}
  <a href="#login">Login</a>
  {/if}
  
  {#if page === "#login"}
  <Login />
  {:else}
  <Todo />
  {/if}
  <!-- <Calculator bind:value={pin} on:submit={handleSubmit} /> -->
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
