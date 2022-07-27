<script>
    import { createEventDispatcher } from 'svelte';
  let count = 0;

  function handleClick() {
    count += 1;
  }
  $: doubled = count * 2;
  $: quadrupled = doubled * 2;


  const dispatch = createEventDispatcher();

	function sayHello() {
		dispatch('message', {
			text: 'Hello world!'
		});
	}
</script>

<button on:click={handleClick}>
  increase
</button>

<button
  on:click={() => {
    count -= 1;
  }}
>
 decrease
</button>
<p>{count} * 2 = {doubled}</p>
<p>{doubled} * 2 = {quadrupled}</p>

<button on:click={sayHello}>
	Click to say hello
</button>