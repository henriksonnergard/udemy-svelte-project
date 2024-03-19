<!-- <script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Henrik";
  let title = "";
  let image = "";
  let description = "";
  let formState = 'empty';

  let createdContacts = [];

  function addContact() {
    if (
      name.trim().length == 0 || 
      title.trim().length == 0 || 
      image.trim().length == 0 || 
      description.trim().length == 0
      ) {
        formState = 'invalid';
        return;
      }
    createdContacts = [...createdContacts, {
      id: Math.random(),
      name: name, 
      jobTitle: title, 
      imageUrl: image, 
      desc: description
    }];
    formState = 'done';
  }

  function deleteFirst() {
    createdContacts = createdContacts.slice(1);
  }

  function deleteLast() {
    createdContacts = createdContacts.slice(0, -1);
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
</div>

<button on:click={addContact}>Add Contact Card</button>
<button on:click={deleteFirst}>Delete First</button>
<button on:click={deleteLast}>Delete Last</button>

{#if formState === 'invalid'}
 <p>There is something wrong with your information, please double check.</p>
{:else}
  <p>Please fill out all required information.</p>
{/if}
<div class="cards-container">
  {#each createdContacts as contact, i (contact.id)}
    <div class="card-wrapper">
      <h2># {i+1}</h2>
      <ContactCard 
        userName={contact.name} 
        jobTitle={contact.jobTitle} 
        description={contact.desc} 
        userImage={contact.imageUrl} 
      />
    </div>
  {:else}
    <p>No contact cards created.</p>
  {/each}
</div> -->

<script>
  let password = '';
  let tempPassword = '';
  let passwords = [];
  let passwordState = 'empty';
  
  function savePassword() {
    if (tempPassword.trim().length == 0) {
      return
    }
    else if (tempPassword.trim().length < 5) {
      passwordState = 'tooShort';
      return
    }
    else if (tempPassword.trim().length > 10) {
      passwordState = 'tooLong';
      return
    }
    passwords = [...passwords, tempPassword];
    passwordState = 'done';
  }

  function removePassword(index) {
    passwords = passwords.filter((pw, idx) => {
      return idx !== index;
    });
  }

</script>

<style>
  .form {
    margin-inline: auto;
    max-width: 35rem;
  }
  .password-error {
    color: red;
  }
</style>

<div class="form">
  <input type="password" bind:value={tempPassword}>
  <button on:click={savePassword} type="button">Save password</button>

  {#if tempPassword === ''}
    <p class="password-error">Please enter a password.</p>
  {:else if tempPassword.length < 5}
    <p class="password-error">Your password needs to be longer than 5 characters.</p>
  {:else if tempPassword.length > 10}
    <p class="password-error">Your password needs to be shorter than 10 characters.</p>
  {:else}
    <p>{tempPassword}</p>
  {/if}
  {#each passwords as pw, i}
    <ul>
      <li on:click={removePassword.bind(this, i)}>{pw}</li>
    </ul>
  {/each}
</div>

<hr>
<h1>Assignment</h1>

<p>Solve these tasks.</p>

<ol>
	<li>Add a password input field and save the user input in a variable.</li>
	<li>Output "Too short" if the password is shorter than 5 characters and "Too long" if it's longer than 10.</li>
	<li>Output the password in a paragraph tag if it's between these boundaries.</li>
	<li>Add a button and let the user add the passwords to an array.</li>
	<li>Output the array values (= passwords) in a unordered list (ul tag).</li>
	<li>Bonus: If a password is clicked, remove it from the list.</li>
</ol>

