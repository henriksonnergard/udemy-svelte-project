<script>
	import ContactCard from "../ContactCard.svelte";

	export let name = "Hånkmaestro";
	export let age = 31;
	export let title = "";
	export let image = "";
	export let description = "";

	$: uppercaseName = name.toUpperCase();

	function incrementAge() {
		age += 1;
	}

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello! I'm {uppercaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change Age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<input type="text" bind:value="{name}">
<input type="text" bind:value="{title}">
<input type="text" bind:value="{image}">
<textarea rows="3" bind:value="{description}"></textarea>

<ContactCard userName="{name}" jobTitle="{title}" jobDescription="{description}" userImage="{image}" />
