<script>
	const tiers = [
		{ name: 'S', color: '#ff7f7f' },
		{ name: 'A', color: '#ffbf7f' },
		{ name: 'B', color: '#ffff7f' },
		{ name: 'C', color: '#7fff7f' },
		{ name: 'D', color: '#7f7fff' },
	];

	function handleDragOver(e) {
		e.preventDefault();
	}

	function handleDrop(e, tier) {
		e.preventDefault();
		const factionId = e.dataTransfer.getData('faction');
		const faction = document.getElementById(factionId);
		if (faction) {
			e.currentTarget.querySelector('.tier-content').appendChild(faction);
		}
	}
</script>

<div class="tier-list">
	{#each tiers as tier}
		<div
			class="tier-row"
			on:dragover={handleDragOver}
			on:drop={(e) => handleDrop(e, tier)}
		>
			<div class="tier-label" style="background-color: {tier.color}">
				{tier.name}
			</div>
			<div class="tier-content"></div>
		</div>
	{/each}
</div>

<style>
	.tier-list {
		width: 100%;
		max-width: 800px;
		margin: 20px auto;
		background: rgba(159, 159, 159, 0.9);
		padding: 10px;
		border-radius: 8px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
	}

	.tier-row {
		display: flex;
		min-height: 80px;
		margin-bottom: 4px;
		border-radius: 4px;
		background-color: #2c2c2c;
	}

	.tier-label {
		width: 60px;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 20px;
		font-weight: bold;
		border-radius: 4px 0 0 4px;
		color: #fff;
		text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
	}

	.tier-content {
		flex-grow: 1;
		padding: 5px;
		display: flex;
		flex-wrap: wrap;
		gap: 5px;
	}

	@media (max-width: 768px) {
		.tier-list {
			margin: 10px;
			padding: 5px;
		}

		.tier-row {
			min-height: 60px;
		}

		.tier-label {
			width: 40px;
			font-size: 16px;
		}
	}
</style>
