<script>
  import { createEventDispatcher } from "svelte";
  import debounce from "debounce-fn";

  const dispatch = createEventDispatcher();
  const debouncedDispatch = debounce(dispatch, { wait: 200 });
  let query = "";

  $: {
    debouncedDispatch("message", { query });
  }
</script>

<div>

  <input bind:value={query} />
</div>
