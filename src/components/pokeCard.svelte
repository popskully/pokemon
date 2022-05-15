<script>
	import { fade } from 'svelte/transition';
	export let pokeman;
</script>

<a
	href={`/pokemon/${pokeman.id}`}
	class="card lg:card-side bg-base-100 border-2 border-gray-500"
	transition:fade
>
	<figure><img class="h-40 w-40" src={pokeman.image} alt={pokeman.name} /></figure>
	<div class="card-body">
		<h2 class="card-title">{pokeman.id}. {pokeman.name}</h2>
		<p>{pokeman.name}</p>
		<div class="card-actions justify-end" />
	</div>
</a>
