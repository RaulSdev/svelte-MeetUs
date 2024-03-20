<script>
  import Header from '../UI/Header.svelte';
  import MeetupGrid from '../Meetups/MeetupGrid.svelte';
  import TextInput from '../UI/TextInput.svelte';
  import Button from '../UI/Button.svelte';

  let title = '';
  let subtitle = '';
  let address = '';
  let email = '';
  let description = '';
  let imageUrl = '';

  let meetups = [
    {
      id: 'm1',
      title: 'Code Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description:
        'in this meetup, we will have some expertat that teach you how to code',
      imageUrl:
        'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi1.wp.com%2Fwww.edutechpost.com%2Fwp-content%2Fuploads%2F2017%2F07%2Ffreecodecamp-banner-thumbnail.png%3Ffit%3D779%252C499&f=1&nofb=1&ipt=41b7bcf1121b34c8459d47ef0144989835119aef610aec5eec66d68e1940e9fb&ipo=images',
      address: 'Algun lugar chido',
      contactEmail: 'code@test.com',
    },
    {
      id: 'm2',
      title: 'Pool Party',
      subtitle: 'Come party at the pool party',
      description: 'pool party for a devs today! come and join us',
      imageUrl:
        'https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.einkaufen-in-leichlingen.de%2Fwp-content%2Fuploads%2F2019%2F07%2FPoolparty.jpg&f=1&nofb=1&ipt=519448b373d8a9ade674966958a3cefe5e64690f2efcacfa09baa6abdfaae648&ipo=images',
      address: 'Algun lugar chido & exotico #2077',
      contactEmail: 'code@test.com',
    },
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address,
    };
    meetups = [newMeetup, ...meetups];
  }
</script>

<Header />

<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      type="text"
      value={title}
      on:input={(event) => (title = event.target.value)}
    />
    <TextInput
      id="subtitle"
      label="Subtitle"
      type="text"
      value={subtitle}
      on:input={(event) => (subtitle = event.target.value)}
    />
    <TextInput
      id="address"
      label="Address"
      type="text"
      value={address}
      on:input={(event) => (address = event.target.value)}
    />
    <TextInput
      id="imageUrl"
      label="Image URL"
      type="text"
      value={imageUrl}
      on:input={(event) => (imageUrl = event.target.value)}
    />
    <TextInput
      id="email"
      label="E-Mail"
      value={email}
      type={email}
      on:input={(event) => (email = event.target.value)}
    />
    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      value={description}
      on:input={(event) => (description = event.target.value)}
    />
    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} />
</main>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>
