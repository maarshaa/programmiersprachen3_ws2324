<script>
	import Card from "./Card.svelte";
	import dinosaurs from "./dinosaur_data.js"; // Import the array directly

	let sortOrder = "name"; // Default sort order
	let funFact = "Klick auf einen Dino, um einen Funfact zu sehen!";
	let selected = "red";

	// Function to handle sorting
	function sort(order) {
		sortOrder = order;
		// Create a new array to trigger reactivity
		const sorted = dinosaurs.sort((a, b) => {
			if (a[sortOrder] < b[sortOrder]) return -1;
			if (a[sortOrder] > b[sortOrder]) return 1;
			return 0;
		});
		console.log(dinosaurs.map((dino) => dino[sortOrder]));
		return sorted;
	}

	function setSortOrder(order) {
		sortOrder = order;
	}

	function updateFunFact(dino) {
		funFact = dino.random_fact;
	}
</script>

<div id="wrapper">
	<main>
		<div id="bar">
			<div id="sort">
				<h5>Sortiere nach:</h5>
				<button
					on:click={() => setSortOrder("height")}
					class="sortButton"
					style="background-color: {sortOrder === 'height'
						? 'rgb(86, 195, 46)'
						: 'rgba(86, 195, 46, 0.4)'}"
					><img src="images/height.png" alt="height" /></button
				>
				<button
					on:click={() => setSortOrder("footprint")}
					class="sortButton"
					style="background-color: {sortOrder === 'footprint'
						? 'rgb(86, 195, 46)'
						: 'rgba(86, 195, 46, 0.4)'}"
				>
					<img src="images/footprint.png" alt="footprint" />
				</button>
				<button
					on:click={() => setSortOrder("years")}
					class="sortButton"
					style="background-color: {sortOrder === 'years'
						? 'rgb(86, 195, 46)'
						: 'rgba(86, 195, 46, 0.4)'}"
					><img src="images/years.png" alt="years" /></button
				>
				<button
					on:click={() => setSortOrder("iq")}
					class="sortButton"
					style="background-color: {sortOrder === 'iq'
						? 'rgb(86, 195, 46)'
						: 'rgba(86, 195, 46, 0.4)'}"
					><img src="images/iq.png" alt="iq" /></button
				>
				<button
					on:click={() => setSortOrder("egg_size")}
					class="sortButton"
					style="background-color: {sortOrder === 'egg_size'
						? 'rgb(86, 195, 46)'
						: 'rgba(86, 195, 46, 0.4)'}"
					><img
						src="images/egg_size.png"
						alt="size of eggs"
					/></button
				>
				<button
					on:click={() => setSortOrder("tooth_size")}
					class="sortButton"
					style="background-color: {sortOrder === 'tooth_size'
						? 'rgb(86, 195, 46)'
						: 'rgba(86, 195, 46, 0.4)'}"
					><img
						src="images/tooth_size.png"
						alt="size of theeth"
					/></button
				>
			</div>
			<div class="funfact"><h5>{funFact}</h5></div>
		</div>

		<div id="cards-container">
			{#if sortOrder === "group"}
				{#each sort("group") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
						class="dinoButtons"
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else if sortOrder === "height"}
				{#each sort("height") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else if sortOrder === "footprint"}
				{#each sort("footprint") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else if sortOrder === "years"}
				{#each sort("years") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else if sortOrder === "iq"}
				{#each sort("iq") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else if sortOrder === "egg_size"}
				{#each sort("egg_size") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else if sortOrder === "tooth_size"}
				{#each sort("tooth_size") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{:else}
				{#each sort("name") as dinosaur}
					<button
						on:click={() => {
							updateFunFact(dinosaur);
						}}
					>
						<Card dino={dinosaur} />
					</button>
				{/each}
			{/if}
		</div>
	</main>
	<footer></footer>
</div>

<style>
	#bar {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding: 0 5rem 2rem 6rem;
	}
	#wrapper {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 5rem;
	}

	#cards-container {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		width: 100%;
	}

	#sort {
		align-items: center;
		display: flex;
		font-size: 2rem;
	}

	#sort button {
		background-color: rgba(86, 195, 46, 0.4);
		border-radius: 5rem;
		padding: 0.5rem;
		margin: 0.5rem;
	}

	#sort button:hover {
		transform: scale(1.5);
		transition: transform 0.3s ease;
		cursor: pointer;
	}

	#sort img {
		height: 3rem;
		width: auto;
	}

	button {
		background-color: transparent;
		border: none;
	}

	.dinoButtons {
		width: auto;
		padding: 2rem;
		border: none;
		margin: 30rem;
	}

	.sortButton:active {
		background-color: salmon;
	}

	.funfact {
		width: 40rem;
		height: auto;
		float: right;
		color: inherit;
		background-color: rgba(134, 134, 134, 0.1);
		border: 1px dashed rgb(96, 166, 55, 0.4);
		padding: 1em;
		margin-bottom: 2rem;
		font-size: 2rem;
	}

	@media (max-width: 100rem) {
		#wrapper {
			display: flex;
			flex-direction: column;
			align-items: center;
			padding: 2rem;
		}
		#sort {
			align-items: center;
			display: flex;
		}
		#bar {
			flex-direction: column;
			align-items: center;
			justify-content: center;
			margin-bottom: -3rem;
		}

		.funfact {
			width: 100%;
			float: none;
			margin-top: 1rem;
		}
		#sort button {
			background-color: rgba(86, 195, 46, 0.4);
			border-radius: 5rem;
			padding: 0.5rem;
			margin: 0.5rem;
		}

		#sort button:hover {
			transform: scale(1.2);
			transition: transform 0.3s ease;
			cursor: pointer;
		}

		#sort img {
			height: 1.5rem;
			width: auto;
		}
	}
</style>
