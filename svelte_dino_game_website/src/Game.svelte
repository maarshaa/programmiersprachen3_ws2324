<script>
	import DinoPicture from "./DinoPictures.svelte";
	import dinosaurs from "./dinosaur_data.js";
	import Info from "./Info.svelte";

	const selected = "rgb(68, 96, 58)";
	const unselected = "beige";

	function getRandomDinosaur() {
		return dinosaurs[Math.floor(Math.random() * dinosaurs.length)];
	}

	function isCurrentDinosaur(dino) {
		alreadyClicked = true;
		correct = dino === currentDinosaur;
		if (!correct && roundPoints > 0) {
			roundPoints--;
		}
	}

	function showResult() {
		correct = true;
		roundPoints = 0;
	}

	function updateDifficulty(level) {
		difficulty = level;
	}

	function reset() {
		correct = false;
		roundPoints = pointsPerRound;
		currentDinosaur = getRandomDinosaur();
		alreadyClicked = false;
	}

	function getRoundPoints() {
		const currentPoints = roundPoints * difficulty;
		totalPoints += currentPoints;
		return currentPoints;
	}

	let alreadyClicked = false;

	let currentDinosaur = getRandomDinosaur();

	let correct = false;
	const pointsPerRound = 5;
	let roundPoints = pointsPerRound;
	let difficulty = 1;

	let totalPoints = 0;
</script>

<div id="wrapper" class="split">
	<main>
		<div id="info-container">
			<h1>Dino Quiz</h1>
			<h5>
				Wähle das richtige Dinobild aus und erhalte Punkte. Du hast drei
				Versuche, findest du den richtigen Dino beim ersten Versuch
				bekommst du die vollen 3 Punkte!
			</h5>

			<div class="difficulty">
				<h5>Wähle die Schwierigkeit aus:</h5>
				<button
					class="difficultyButton"
					on:click={reset}
					on:click={() => updateDifficulty(1)}
					style="background: {difficulty >= 1
						? selected
						: unselected}"
				></button>
				<button
					class="difficultyButton"
					on:click={reset}
					on:click={() => updateDifficulty(2)}
					style="background: {difficulty >= 2
						? selected
						: unselected}"
				></button>
				<button
					class="difficultyButton"
					on:click={reset}
					on:click={() => updateDifficulty(3)}
					style="background: {difficulty >= 3
						? selected
						: unselected}"
				></button>
				<button
					class="difficultyButton"
					on:click={reset}
					on:click={() => updateDifficulty(4)}
					style="background: {difficulty >= 4
						? selected
						: unselected}"
				></button>
				<button
					class="difficultyButton"
					on:click={reset}
					on:click={() => updateDifficulty(5)}
					style="background: {difficulty >= 5
						? selected
						: unselected}"
				></button>
				<button
					class="difficultyButton"
					on:click={reset}
					on:click={() => updateDifficulty(6)}
					style="background: {difficulty >= 6
						? selected
						: unselected}"
				></button>
			</div>

			<Info
				dino={currentDinosaur}
				{correct}
				{difficulty}
				clicked={alreadyClicked}
			/>

			<div>
				<div class="feedback">
					<div>
						<h5>
							Punkte für die Runde: {correct
								? getRoundPoints()
								: ""}
						</h5>
						<h5>Total: {totalPoints}</h5>
					</div>
					<button class="playButton" on:click={reset}>
						nächster dino</button
					>

					<button class="playButton" on:click={showResult}>
						Lösung
					</button>
				</div>
				<div id="picture-container">
					{#each dinosaurs as dinosaur}
						<button
							class="dinoButtons"
							on:click={() => isCurrentDinosaur(dinosaur)}
							><DinoPicture
								dino={dinosaur}
								{currentDinosaur}
								{correct}
							/></button
						>
					{/each}
				</div>
			</div>
		</div>
	</main>
</div>

<style>
	#wrapper {
		display: flex;
		flex-direction: row;
		padding: 5rem;
	}

	.feedback {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		grid-template-rows: repeat(1, 1fr);
		margin: 1rem 0 3rem 0;
		align-items: center;
	}

	#info-container {
		display: flex;
		flex-direction: column;
	}

	#picture-container {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}

	.difficulty {
		display: flex;
		max-width: 40rem;
		flex-direction: row;
		align-items: center;
		margin: 1rem 0;
		justify-content: space-between;
		width: 100%;
	}

	button {
		width: flex;
		border: none;
		padding: 0px;
		margin: 1rem;
	}

	button:hover {
		transform: scale(1.05);
		transition: transform 0.3s ease;
		background-color: rgb(68, 96, 58);
		color: white;
		cursor: pointer;
	}

	.difficultyButton {
		width: 30px;
		height: 30px;
		border: none;
		background-color: rgb(148, 186, 131);
		border-radius: 100%;
	}

	.difficultyButton:hover {
		transform: scale(1.05);
		transition: transform 0.3s ease;
		background-color: rgb(68, 96, 58);
		color: white;
		cursor: pointer;
		float: left;
	}

	.playButton {
		width: flex;
		height: flex;
		padding: 10px 50px 10px 50px;
		border: none;
		background-color: rgba(134, 134, 134, 0.1);
		border: 1px dashed rgb(96, 166, 55, 0.4);
		border-radius: 5px;
	}

	.dinoButtons {
		border: none;
		background-color: transparent;
		margin: 1%;
		float: left;
	}

	.dinoButtons:hover {
		transform: scale(1.05);
		transition: transform 0.3s ease;
		background-color: transparent;
		cursor: pointer;
	}
</style>
