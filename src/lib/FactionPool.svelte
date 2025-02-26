<script>
	import { onMount } from 'svelte';

	const factions = [
		{
			id: 'marquise',
			name: 'Marquise de Cat',
			image: '/factions/marquise.png',
		},
		{
			id: 'eyrie',
			name: 'Eyrie Dynasties',
			image: '/factions/eyrie.png',
		},
		{
			id: 'woodland',
			name: 'Woodland Alliance',
			image: '/factions/woodland.png',
		},
		{
			id: 'vagabond',
			name: 'Vagabond',
			image: '/factions/vagabond.png',
		},
		{
			id: 'riverfolk',
			name: 'Riverfolk Company',
			image: '/factions/riverfolk.png',
		},
		{
			id: 'lizard',
			name: 'Lizard Cult',
			image: '/factions/lizard.png',
		},
		{
			id: 'corvid',
			name: 'Corvid Conspiracy',
			image: '/factions/corvid.png',
		},
		{
			id: 'duchy',
			name: 'Underground Duchy',
			image: '/factions/duchy.png',
		},
	];

	let factionPool;

	onMount(() => {
		// Store initial state of pool for reset functionality
		factionPool = document.querySelector('.faction-pool');
	});

	function handleDragStart(e, faction) {
		e.dataTransfer.setData('faction', faction.id);
	}

	function handleDragOver(e) {
		e.preventDefault();
	}

	function handleDrop(e) {
		e.preventDefault();
		const factionId = e.dataTransfer.getData('faction');
		const faction = document.getElementById(factionId);
		if (faction) {
			e.currentTarget.appendChild(faction);
		}
	}

	function resetTierList() {
		const allFactions = document.querySelectorAll('.faction-card');
		allFactions.forEach((faction) => {
			factionPool.appendChild(faction);
		});
	}

	function saveTierList() {
		const tierList = document.querySelector('.tier-list');
		if (!tierList) return;

		// Use html2canvas to capture the tier list
		import('html2canvas').then((module) => {
			const html2canvas = module.default;
			html2canvas(tierList, {
				backgroundColor: null,
				scale: 2, // Higher quality
			}).then((canvas) => {
				const link = document.createElement('a');
				link.download = 'root-tier-list.png';
				link.href = canvas.toDataURL();
				link.click();
			});
		});
	}
</script>

<div class="faction-pool" on:dragover={handleDragOver} on:drop={handleDrop}>
	{#each factions as faction}
		<div
			id={faction.id}
			class="faction-card"
			draggable="true"
			on:dragstart={(e) => handleDragStart(e, faction)}
		>
			<img src={faction.image} alt={faction.name} />
			<span>{faction.name}</span>
		</div>
	{/each}
</div>

<div class="button-container">
	<button on:click={resetTierList}>Reset Tier List</button>
	<button on:click={saveTierList}>Save as Image</button>
</div>

<style>
	.faction-pool {
		width: 800px;
		margin: 20px auto;
		padding: 20px;
		background-color: rgba(44, 44, 44, 0.9);
		border-radius: 8px;
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
	}

	.faction-card {
		width: 120px;
		padding: 10px;
		border-radius: 4px;
		cursor: move;
		text-align: center;
	}

	.faction-card img {
		width: 100px;
		height: 100px;
		object-fit: contain;
		border-radius: 4px;
	}

	.faction-card span {
		display: block;
		margin-top: 5px;
		font-size: 14px;
		color: #fff;
		text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.8);
	}

	.button-container {
		width: 800px;
		margin: 20px auto;
		display: flex;
		gap: 10px;
		justify-content: center;
	}

	button {
		padding: 10px 20px;
		font-size: 16px;
		border: none;
		border-radius: 4px;
		background-color: #4a4a4a;
		color: white;
		cursor: pointer;
		transition: background-color 0.2s;
	}

	button:hover {
		background-color: #5a5a5a;
	}
</style>
