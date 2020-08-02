<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";
  import EditMeetup from "./Meetups/EditMeetup.svelte";

  let meetups = [];

  let editMode = null;

  function addMeetUp(event) {
    const newMeetUp = {
      id: Math.random().toString(),
      title: event.detail.title,
      subtitle: event.detail.subtitle,
      address: event.detail.address,
      description: event.detail.description,
      contactEmail: event.detail.contactEmail,
      isFavorite: false,
    };

    meetups = [...meetups, newMeetUp];

    editMode = null;
  }

  function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = meetups.find((c) => c.id === id);
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    meetups = meetups;
  }

  function cancelEdit() {
    editMode = null;
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  .meetup-controls {
    margin: 1rem;
  }
</style>

<Header />

<main>
  <div class="meetup-controls">
    <Button
      on:click={() => {
        editMode = 'add';
      }}>
      New Meetup
    </Button>
  </div>
  {#if editMode === 'add'}
    <EditMeetup on:save={addMeetUp} on:cancel={cancelEdit} />
  {/if}
  <MeetupGrid {meetups} on:toggle-favorite={toggleFavorite} />
</main>
