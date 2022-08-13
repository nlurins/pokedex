<script>
	import { pokemon } from '../stores/pokestore.js';
	import PokeCard from '../components/pokeCard.svelte';

	let searchTerm = '';
	let filteredPokemon = [];

	$: {
		console.log(searchTerm);
		if (searchTerm) {
			filteredPokemon = $pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			filteredPokemon = [...$pokemon];
		}
	}
</script>

<svelte:head>
	<title>Pokedex</title>
</svelte:head>
<h1 class="font-bold text-4xl my-8 uppercase text-center">Pokedex</h1>
<input
	class="w-full rounded-md text-lg p-4 border-2 border-gray-200"
	bind:value={searchTerm}
	type="text"
	placeholder="Search Pokemon"
/>
<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1 ">
	{#each filteredPokemon as pokeman}
		<PokeCard {pokeman} />
	{/each}
</div>
