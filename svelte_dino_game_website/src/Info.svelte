<script>
	export let dino;
	export let correct;
	export let difficulty;
	export let clicked;
	const imagePath = `/images/${dino.name}.jpg`;
</script>

<div class="card-container">
	<div
		class="card-content"
		style="background:{clicked
			? correct
				? 'rgba(107,187,100,0.5)'
				: 'rgba(205,69,69,0.5)'
			: 'rgba(134, 134, 134, 0.2)'}"
	>
		<div class="card-title">
			<h5>{dino.name}</h5>
		</div>
		<div class="card-group">
			{correct || difficulty < 5 ? dino.group : "???"}
		</div>
		<div class="info">
			{correct || difficulty < 3 ? dino.random_fact : "???"}
		</div>
		<div class="stats-wrapper">
			<div class="card-stat center-content">
				<img src="images/height.png" alt="height" />
			</div>
			<div class="card-val center-content">
				{correct || difficulty < 5 ? dino.height : "???"}
			</div>

			<div class="card-stat center-content">
				<img src="images/footprint.png" alt="footprint" />
			</div>
			<div class="card-val center-content">
				{correct || difficulty < 4 ? dino.footprint : "???"}
			</div>

			<div class="card-stat center-content">
				<img src="images/years.png" alt="years since extinction" />
			</div>
			<div class="card-val center-content">
				{correct || difficulty < 4 ? dino.years : "???"}
			</div>

			<div class="card-stat center-content">
				<img src="images/iq.png" alt="eq times 100" />
			</div>
			<div class="card-val center-content">{dino.iq}</div>

			<div class="card-stat center-content bottom-left">
				<img src="images/egg_size.png" alt="egg size" />
			</div>
			<div class="card-val center-content">
				{correct || difficulty < 5 ? dino.egg_size : "???"}
			</div>

			<div class="card-stat center-content">
				<img src="images/tooth_size.png" alt="number of teeth" />
			</div>
			<div class="card-val center-content bottom-right">
				{correct || difficulty < 3 ? dino.tooth_size : "???"}
			</div>
		</div>
	</div>
</div>

<style>
	.card-container {
		width: 100%;
		height: 100%;
	}
	.card-content {
		width: 100%;
		height: fit-content;
		padding: 2rem;
		margin: 2rem 0;
		border-radius: 10px;
		background-color: rgba(255, 255, 255, 0.186);
		display: grid;
		grid-template-columns: 1fr 8fr;
		grid-template-rows: 2fr 3fr;
		grid-template-areas:
			"name tabelle"
			"info tabelle";
		gap: 0rem;
	}

	.card-title {
		grid-area: name;
	}

	.stats-wrapper {
		grid-area: stat;
		max-height: 100%;
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		grid-template-rows: repeat(1, 1fr);
		grid-area: tabelle;
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
		align-items: center;
		justify-content: center;
	}

	.info {
		grid-area: info;
		font-size: 1.2em;
		font-weight: 600;
	}

	.center-content {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	@media (max-width: 90rem) {
		.card-content {
			width: 100%;
			height: fit-content;
			border-radius: 10px;
			border: 1px solid #989898;
			background-color: rgba(255, 255, 255, 0.186);
			display: grid;
			grid-template-columns: 1fr 1fr;
			grid-template-rows: 1fr 5fr;
			grid-template-areas:
				"name info"
				"tabelle tabelle";
			gap: 0rem;
		}
		.stats-wrapper {
			grid-area: stat;
			max-height: 100%;
			display: grid;
			grid-template-columns: repeat(4, 1fr);
			grid-template-rows: repeat(3, 1fr);
			grid-area: tabelle;
			padding: 0 1rem;
			padding-top: -1rem;
		}
	}
</style>
