<script>
  import Button from "../UI/Button.svelte";
  import Badge from "../UI/Badge.svelte";
  import { createEventDispatcher } from "svelte";

  export let id;
  export let title;
  export let subtitle;
  export let description;
  export let contactMail;
  export let address;
  export let isFavorite;

  const dispatch = createEventDispatcher();
</script>

<article>
  <header>
    <h1>
      {title}
      {#if isFavorite === true}
        <Badge>Favorite</Badge>
      {/if}
    </h1>
    <h2>{subtitle}</h2>
    <p>{address}</p>
  </header>
  <div class="image">
    <img src="" alt={title} />
  </div>
  <div class="content">
    <p>{description}</p>
  </div>
  <footer>
    <Button href="mailto:{contactMail}">Contact</Button>
    <Button
      on:click={() => {
        dispatch('toggle-favorite', id);
      }}>
      {isFavorite === true ? 'Unfavorite' : 'Favorite'}
    </Button>
    <Button
      on:click={() => {
        dispatch('show-details', id);
      }}>
      Show Details
    </Button>
  </footer>
</article>
