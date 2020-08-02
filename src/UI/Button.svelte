<script>
  export let type = "button";
  export let href = null;
</script>

{#if href}
  <a {href}>
    <slot />
  </a>
{:else}
  <button {type} on:click>
    <slot />
  </button>
{/if}
