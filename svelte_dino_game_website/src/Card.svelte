<script>
	export let dino;
	import darkMode from "./App.svelte";
	const imagePath = `/images/${dino.name}.png`;
</script>

<div class="card-container">
	<div class="card-content">
		<div class="card-title">
			<h3>{dino.name}</h3>
		</div>
		<div class="card-image center-content">
			<img src={imagePath} alt="Image of a {dino.name}" />
		</div>
		<div class="stats-wrapper">
			<div class="card-stat center-content">
				<img src="images/height.png" alt="height" />
			</div>
			<div class="card-val center-content">
				<h4>{dino.height}</h4>
			</div>

			<div class="card-stat center-content">
				<img src="images/footprint.png" alt="footprint" />
			</div>
			<div class="card-val center-content"><h4>{dino.footprint}</h4></div>

			<div class="card-stat center-content">
				<img src="images/years.png" alt="years since extinction" />
			</div>
			<div class="card-val center-content"><h4>{dino.years}</h4></div>

			<div class="card-stat center-content">
				<img src="images/iq.png" alt="eq times 100" />
			</div>
			<div class="card-val center-content"><h4>{dino.iq}</h4></div>

			<div class="card-stat center-content bottom-left">
				<img src="images/egg_size.png" alt="egg size" />
			</div>
			<div class="card-val center-content"><h4>{dino.egg_size}</h4></div>

			<div class="card-stat center-content">
				<img src="images/tooth_size.png" alt="number of teeth" />
			</div>
			<div class="card-val center-content bottom-right">
				<h4>{dino.tooth_size}</h4>
			</div>
		</div>
	</div>
</div>

<style>
	.card-container {
		width: 100%;
		height: 100%;
		align-items: center;
		padding: 0 5rem;
		background-color: inherit;
		color: inherit;
	}
	.card-content {
		width: 100%;
		height: fit-content;
		margin: 1rem;
		border-radius: 10px;
		border: 1px solid #989898;
		background-color: rgba(255, 255, 255, 0.186);
		display: grid;
		grid-template-columns: 1fr 8fr;
		grid-template-rows: 2fr 3fr;
		grid-template-areas:
			"dinobild dinoname"
			"dinobild tabelle";
		gap: 0rem;
	}

	.card-content:hover {
		transform: scale(1.05);
		transition: transform 0.3s ease;
		cursor: pointer;
	}

	.card-title {
		margin: auto;
		grid-area: dinoname;
		margin-left: 3rem;
	}

	.card-image {
		grid-area: dinobild;
		height: 100%;
		align-self: flex-start;
	}

	.card-image img {
		height: 15rem;
	}

	.stats-wrapper {
		grid-area: stat;
		max-height: 100%;
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		grid-template-rows: repeat(1, 1fr);
		grid-area: tabelle;
		padding: 0 2rem;
		padding-top: -1rem;
	}

	.card-stat {
		height: 6rem;
		background-color: rgb(84, 140, 47);
		border: 1px solid rgb(74, 74, 74);
		border-radius: 1rem 0 0 1rem;
		margin-top: 1rem;
		margin-left: 1rem;
	}

	.card-val {
		width: auto;
		max-height: 6rem;
		border-radius: 0 1rem 1rem 0;
		padding-top: 1.5rem;
		padding: 1rem;
		background-color: rgba(255, 255, 255, 0.268);
		border: 1px solid rgb(58, 58, 58);
		margin-right: 1rem;
		margin-top: 1rem;
		font-size: 2em;
		color: inherit;
	}

	.card-stat img {
		height: 8rem;
		max-height: 4rem;
		width: auto;
	}

	.center-content {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	@media screen and (max-width: 130rem) {
		.card-container {
			width: 100%;
			height: 100%;
			align-items: center;
			padding: 1rem;
		}
		.card-content {
			width: 26rem;
			height: 42rem;
			margin: 0.5rem;
			border-radius: 10px;
			border: 0.5px solid #808080;
			background-color: rgba(255, 255, 255, 0.2);
			display: grid;
			grid-template-columns: 1fr 5fr;
			grid-template-rows: 1fr 5fr 6fr;
			grid-template-areas:
				"dinoname dinoname"
				"dinobild dinobild"
				"tabelle tabelle";
		}
		.card-title {
			grid-area: dinoname;
			margin: 0rem;
			align-items: center;
		}

		.card-image {
			grid-area: dinobild;
			padding: 3px;
		}

		.card-image img {
			height: auto;
			width: 100%;
		}

		.stats-wrapper {
			grid-area: stat;
			max-height: 100%;
			display: grid;
			grid-template-columns: repeat(4, 1fr);
			grid-template-rows: repeat(3, 1fr);
			grid-area: tabelle;
			gap: 0.5rem;
			padding: 0 0 0 3rem;
		}

		.card-val {
			width: 5rem;
			max-height: 5rem;
			border-radius: 0 1rem 1rem 0;
			padding-top: 1.5rem;
			padding: 1rem;
			background-color: rgba(255, 255, 255, 0.268);
			border: 1px solid rgb(58, 58, 58);
			margin-right: 1rem;
			margin-top: 1rem;
		}
		.card-stat {
			height: 5rem;
			width: 5rem;
			background-color: rgb(84, 140, 47);
			border: 1px solid rgb(74, 74, 74);
			border-radius: 1rem 0 0 1rem;
			margin-top: 0.5rem;
			margin-right: -2rem;
			margin-left: -1rem;
		}
		.card-stat img {
			height: 3rem;
			width: auto;
		}

		.card-val {
			height: auto;
			color: inherit;
			background-color: inherit;
			margin: 0px;
			float: right;
			margin-top: 0.5rem;
			margin-right: 2rem;
			margin-left: 1rem;
		}

		.center-content {
			display: flex;
			align-items: center;
			justify-content: center;
		}
	}
</style>
