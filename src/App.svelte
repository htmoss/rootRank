<script>
	import TierList from './lib/TierList.svelte';
	import FactionPool from './lib/FactionPool.svelte';
</script>

<svelte:head>
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
</svelte:head>

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
		background-image: url('./forest-background.png');
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		opacity: 0.3;
		z-index: -1;
	}

	main {
		width: 100%;
		max-width: 900px;
		margin: 0 auto;
		padding: 20px;
		position: relative;
		box-sizing: border-box;
	}

	h1 {
		text-align: center;
		color: #fff;
		text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
		font-size: 2rem;
		margin: 1rem 0;
	}

	@media (max-width: 768px) {
		main {
			padding: 10px;
		}

		h1 {
			font-size: 1.5rem;
		}
	}
</style>
