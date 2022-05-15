<script>
	import Nav from '../components/Nav.svelte';
</script>

<Nav />

<div class="px-8 mx-auto">
	<slot />
</div>

<style>
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
