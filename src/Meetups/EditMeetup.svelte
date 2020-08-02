<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";
  import Modal from "../UI/Modal.svelte";

  let title = "Title 1";
  let subtitle = "Subtitle 1";
  let description = "Desc 1";
  let address = "Addr 1";
  let contactEmail = "Email1@karakkof.com";

  const dispatch = createEventDispatcher();

  function submitForm() {
    dispatch("save", {
      title: title,
      subtitle: subtitle,
      description: description,
      address: address,
      contactEmail: contactEmail,
    });
  }

  function cancelEdit() {
    dispatch("cancel");
  }
</script>

<style>
  form {
    width: 100%;
  }
</style>

<Modal title="Edit Meetup Data" on:cancel>
  <form on:submit|preventDefault={submitForm}>

    <TextInput
      id="title"
      label="Title"
      value={title}
      on:input={(event) => (title = event.target.value)} />

    <TextInput
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={(event) => (subtitle = event.target.value)} />

    <TextInput
      id="address"
      label="Address"
      value={address}
      on:input={(event) => (address = event.target.value)} />

    <TextInput
      id="email"
      label="Email"
      inputType="email"
      value={contactEmail}
      on:input={(event) => (contactEmail = event.target.value)} />

    <TextInput
      controlType="textarea"
      id="desc"
      label="Description"
      rows="5"
      value={description}
      on:input={(event) => (description = event.target.value)} />

  </form>
  <div slot="footer">
    <Button type="button" on:click={submitForm}>Add</Button>
    <Button type="button" on:click={cancelEdit}>Cancel</Button>
  </div>
</Modal>
