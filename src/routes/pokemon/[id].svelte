<script context="module">
	export async function load({ params }) {
		const id = params.id;
		const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
		const res = await fetch(url);
		const pokeman = await res.json();
		console.log(pokeman);
		return { props: { pokeman } };
	}
</script>

<script>
	export let pokeman;
    const type = pokeman.types[0].type.name;
</script>

<h1 class="font-bold text-4xl my-8 uppercase text-center">{pokeman.name}</h1>
<div class="flex flex-col items-center">
    <p>
        Type <strong>{type}</strong> | Height: <strong>{pokeman.height}</strong>
        | Weight: <strong>{pokeman.weight}</strong>
    </p>
    <img class="h-60 w-60" src={pokeman.sprites['front_default']} alt={pokeman.name} />
</div>
