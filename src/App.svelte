<script>
	import TierList from './lib/TierList.svelte';
	import FactionPool from './lib/FactionPool.svelte';
</script>

<div class="background"></div>

<main>
	<h1>Root Faction Tier List</h1>
	<TierList />
	<FactionPool />
</main>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		min-height: 100vh;
		background-color: #2c3e50;
	}

	.background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-image: url('/forest-background.png');
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		opacity: 0.3;
		z-index: -1;
	}

	main {
		max-width: 900px;
		margin: 0 auto;
		padding: 20px;
		position: relative;
	}

	h1 {
		text-align: center;
		color: #fff;
		text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
	}
</style>
