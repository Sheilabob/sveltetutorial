<script>
	import Modal from './Modal.svelte';


	let people = [
		{ name: "yoshi", beltColor: 'black', age: 25, id: 1 },
		{ name: "mario", beltColor: 'orange', age: 45, id: 2 },
		{ name: "luigi", beltColor: 'brown', age: 35, id: 3 },
	];

	const handleClick = (id) => {
		// delte the person from people
		people = people.filter((person) => person.id != id);
	}

</script>

<Modal />
<main>
	<div>
		{#each people as person}
			<div>
				<h4>{person.name}</h4>
				{#if person.beltColor === 'black'}
				<p><strong>Master Ninja</strong></p>
				{/if}
				<p>{person.age} years old, {person.beltColor} belt.</p>
				<button on:click={() => {handleClick(person.id);}}>delete</button>
			</div>
		{:else}
			<p>THere are no people to show . . .</p>
		{/each}
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>