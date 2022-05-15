<script context="module">
	export async function load({ params }) {
		const url = 'https://pokeapi.co/api/v2/pokemon?limit=150';
		const res = await fetch(url);
		const data = await res.json();
		const loadedPokemon = data.results.map((data, index) => {
			return {
				name: data.name,
				id: index + 1,
				image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${
					index + 1
				}.png`
			};
		});
		return { props: { pokemon: loadedPokemon } };
	}
</script>

<script>
	export let pokemon;
	import PokeCard from '../components/pokeCard.svelte';

	let searchTerm = '';
	let filteredPokemon = [];

	$: {
		if (searchTerm) {
			// search
			filteredPokemon = pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			filteredPokemon = [...pokemon];
		}
	}
</script>

<svelte:head>
	<title>Pokidex Svelte App</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 font-bold">Pokedex Api</h1>

<input
	type="text"
	placeholder="Search for a Pokemon"
	class="flex mx-auto mb-8 input input-bordered border-2 w-full max-w-xs"
	bind:value={searchTerm}
/>

<div class="grid gap-4 md:grid-cols-3 grid-cols-1 py-4">
	{#each filteredPokemon as pokeman}
		<PokeCard {pokeman} />
	{/each}
</div>
