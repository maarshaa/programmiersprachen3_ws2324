<script>
	import { createClient } from "pexels";

	let funnyDino = "";

	async function setFunnyDino() {
		const client = createClient(
			"zG18Ak1HWDiMYUYhnYXqj9WyRa9czE198ytfDg2ybvlqFHxzLNhLES7k"
		);

		const query = "dino";
		let dinoId;

		client.photos.search({ query, per_page: 1000 }).then((photos) => {
			// @ts-ignore
			const numberOfResults = photos.photos.length;
			const randomIndex = Math.floor(Math.random() * numberOfResults);
			// @ts-ignore
			dinoId = photos.photos[randomIndex].id;
			client.photos.show({ id: dinoId }).then((photo) => {
				// @ts-ignore
				funnyDino = photo.src.original;
			});
		});
	}
	setFunnyDino();
	console.log(funnyDino);
</script>

<main>
	<div id="wrapper">
		<div id="content">
			<div class="left">
				<div id="upper">
					<h1>Willkommen auf DinoDudes.de</h1>
					<h1 class="gap">
						- der ultimativen Quelle für Dino-Wissen und spaßigen
						Saurier-Quatsch! 🦖🎉
					</h1>
					<h5 class="gap">
						Also schnall dich an, halt deine virtuelle Schaufel fest
						und mach dich bereit für eine Dino-Safari der besonderen
						Art! Bei DinoDudes.de garantieren wir nicht nur Wissen,
						sondern auch jede Menge Spaß. Lass uns die Dinos wieder
						zum Leben erwecken – zumindest digital! Bist du bereit,
						in die faszinierende Welt der Dinosaurier einzutauchen?
						Hier bei DinoDudes.de findest du nicht nur trockene
						Fakten, sondern auch jede Menge Spaß und Unterhaltung
						rund um die gigantischen Urzeitbewohner.
					</h5>
				</div>
			</div>
			<div class="left gap">
				<h5 class="text">
					🦖 Dino-Quartett: Spiele unser Dino-Quartett und finde
					heraus, welcher Dino der Größte, der Älteste oder der
					Intelligenteste ist. Wähle aus verschiedenen
					Schwierigkeitsgraden und finde heraus, ob du ein echter
					Dino-Experte bist!
				</h5>
				<a class="goButton" href="#/game">
					<h4>Zum Spiel ></h4>
				</a>
				<h5 class="text">
					🦕 Dino-Info: Hier findest du alle Informationen zu den
					verschiedenen Dino-Arten. Von Stegosaurus bis T-Rex – hier
					erfährst du alles, was du schon immer über die
					Urzeitgiganten wissen wolltest.
				</h5>

				<a class="goButton" href="#/quartet">
					<h4>Übersicht ></h4>
				</a>
			</div>
		</div>
		<div class="right">
			<button class="randomButton" on:click={setFunnyDino}>
				Noch nicht genug? Lass dir einen zufälliges Dinobild anzeigen!
				<div class="pexels">
					<img src="https://images.pexels.com/lib/api/pexels.png" />
				</div>
			</button>
			<div id="randomDino" class="right">
				<img src={funnyDino} alt="Funny random dino image" />
				<a href="https://www.pexels.com"> </a>
			</div>
		</div>
	</div>
</main>

<style>
	.gap {
		margin-bottom: 3rem;
	}
	.text {
		margin-top: 6rem;
	}
	#wrapper {
		display: flex;
		margin: 5rem;
	}

	.left {
		order: 1;
		flex: 100%;
		margin: -3rem 0 0 -3rem;
	}

	#upper {
		grid-area: upper;
	}

	.right {
		width: fit-content;
		border: 1px dashed rgb(96, 166, 55, 0.4);
		border-radius: 1rem;
		order: 2;
		flex: 30%;
		min-width: 40%;
		height: fit-content;
		margin: 1rem;
	}
	#randomDino {
		width: flex;
		height: fit-content;
		border: none;
		background-color: transparent;
		margin: 2rem;
	}

	#randomDino img {
		width: 100%;
		height: flex;
		border-radius: 1rem;
		margin: 0;
	}
	.randomButton {
		width: flex;
		height: fit-content;
		border: none;
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		grid-template-rows: repeat(1, 1fr);
		background-color: rgba(134, 134, 134, 0.1);
		border: 1px dashed rgb(96, 166, 55, 0.4);
		border-radius: 5px;
		margin: 2rem;
		align-items: center;
	}

	a {
		color: inherit;
		margin: 1rem 0;
	}

	@media (max-width: 90rem) {
		/* Mobile view */
		#wrapper {
			flex-direction: column;
			margin: 1rem;
		}

		.left {
			width: 120%;
			padding: 0rem;
		}
	}

	#content {
		padding: 5rem;
		width: 100%;
		height: auto;
	}

	button {
		border: none;
	}

	button:hover {
		transform: scale(1.05);
		transition: transform 0.3s ease;
		cursor: pointer;
	}

	.goButton {
		width: 100%;
		height: flex;
		background-color: rgba(134, 134, 134, 0.1);
		border: 1px dashed rgb(96, 166, 55, 0.4);
		border: none;
		border-radius: 0.5rem;
		margin-top: 1rem;
	}

	.pexels img {
		width: 20%;
		height: auto;
		float: right;
	}
</style>
