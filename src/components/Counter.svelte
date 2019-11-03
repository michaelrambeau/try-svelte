<script>
  export let initialCount = 0;
  let count = initialCount;

  function handleClick() {
    count = count + 1;
  }

  function handleReset() {
    count = initialCount;
  }

  $: doubled = count * 2;
  $: if (count >= 10) {
    alert(`count is dangerously high!`);
    count = 9;
  }
</script>

<div class="card">
  <header>{count} {doubled}</header>
  <button on:click={handleClick}>Increment</button>
  <button on:click={handleReset}>Reset</button>
</div>
