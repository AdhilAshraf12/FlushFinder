<script>
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/FlushFinder.png" />
</svelte:head>

{@render children?.()}

<style>
	* {
		font-family: 'Ubuntu';
	}
</style>
