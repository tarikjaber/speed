<script>
  import { createEventDispatcher } from "svelte";
  
  const dispatch = createEventDispatcher();

  const done = () => {
    dispatch("done")
  }
</script>

<button on:click={done}>
  Done
</button>
