<script>
  import { createEventDispatcher } from "svelte";
  import Button from "./Button.svelte";

  export let title;

  const dispatch = createEventDispatcher();

  function closeModal() {
    dispatch("cancel");
  }
</script>

<style>

</style>

<div class="modal-backdrop" on:click={closeModal} />
<div class="modal">
  <h1>{title}</h1>
  <div class="content">
    <slot />
  </div>
  <footer>
    <slot name="footer">
      <Button on:click={closeModal}>Close</Button>
    </slot>
  </footer>
</div>
