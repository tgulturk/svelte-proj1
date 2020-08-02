<script>
  export let controlType = "input";
  export let inputType = "text";
  export let id;
  export let label;
  export let rows = 3;
  export let value;
</script>

<style>

</style>

<div class="form-control">
  <label for={id}>{label}</label>
  {#if controlType === 'textarea'}
    <textarea {rows} {id} {value} on:input />
  {:else}
    <input type={inputType} {id} {value} on:input />
  {/if}
</div>
