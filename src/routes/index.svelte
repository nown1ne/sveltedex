<script context="module">
	export async function load({ params }) {
		const url = 'https://pokeapi.co/api/v2/pokemon?limit=251';
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
	import PokemanCard from '../components/pokemanCard.svelte';
	export let pokemon;

	let searchTerm = '';
	let filteredPokemon = [];

	$: {
		if (searchTerm) {
			filteredPokemon = pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			filteredPokemon = [...pokemon];
		}
	}
</script>

<svelte:head>
	<title>Pokedex</title>
</svelte:head>

<input
	class="w-full rounded-md text-lg p-4 mt-12 shadow-xl bg-offwhite border-1 border-gray-200
    dark:bg-slate-800 dark:text-gray-100 dark:border-black"
	type="text"
	bind:value={searchTerm}
	placeholder="Search Pokedex"
/>


<div class="py-4 grid gap-4 md:grid-cols-3 grid-cols-1">
	{#each filteredPokemon as pokeman}
		<PokemanCard {pokeman} />
	{/each}
</div>
