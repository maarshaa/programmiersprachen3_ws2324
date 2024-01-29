<script>
	import Router, { location, link } from "svelte-spa-router";
	import Game from "./Game.svelte";
	import Home from "./Home.svelte";
	import Quartet from "./Quartet.svelte";
	// import { page } from "$app/stores";

	let darkMode = true;
	const selectedColor = "rgba(96, 166, 55, 0.5)";
	const unselectedColor = "inherit";
	let selected = "Startseite";

	const routes = {
		"/": Home,
		"/game": Game,
		"/quartet": Quartet,
	};

	function toggleDarkMode() {
		darkMode = !darkMode;
	}
</script>

<div id="wrapper" class={darkMode ? "dark-mode" : ""}>
	<header>
		<link rel="icon" href="./images/Logo.png" />
		<nav>
			<img
				id="logo"
				src="images/LogoGreen.png"
				alt="Logo der Dino Quartett Website"
			/>
			<div id="title">DINO DUDES</div>
			<div class="menu">
				<a
					class="navigationButton"
					href="index.html"
					style="color: {$location.includes('/home')
						? selectedColor
						: unselectedColor}"
				>
					<h4>Home</h4>
				</a>
				<a
					class="navigationButton"
					href="#/quartet"
					style="color: {$location.includes('/quartet')
						? selectedColor
						: unselectedColor}"
				>
					<h4>Übersicht</h4>
				</a>
				<a
					class="navigationButton"
					href="#/game"
					style="color: {$location.includes('/game')
						? selectedColor
						: unselectedColor}"
				>
					<h4>Spiel</h4>
				</a>
			</div>
		</nav>
		<button class="modeButton" on:click={toggleDarkMode}>
			{#if darkMode}
				<img src="images/sun.png" alt="Light Mode" />
			{:else}
				<img src="images/moondunkel.png" alt="Dark Mode" />
			{/if}
		</button>
	</header>

	<main>
		<Router {routes} />
	</main>
	<footer>
		<div class="legend">
			<img src="images/height.png" alt="height" />
			Höhe in Metern
		</div>
		<div class="legend">
			<img src="images/footprint.png" alt="footprint" />
			Fußabdruck in cm
		</div>
		<div class="legend">
			<img src="images/years.png" alt="years since extinction" />
			Jahre seit Aussterben in Millionen
		</div>
		<div class="legend">
			<img src="images/iq.png" alt="eq times 100" />
			Intelligenzquotient (1-50)
		</div>
		<div class="legend">
			<img src="images/egg_size.png" alt="egg size" />
			Eigröße in cm
		</div>
		<div class="legend">
			<img src="images/tooth_size.png" alt="number of teeth" />
			Größe des größten Zahns in cm
		</div>
	</footer>
</div>

<style>
	.navigationButton {
		background-color: transparent;
		border: none;
		color: inherit;
		padding: 0 1rem 0 1rem;
	}
	.navigationButton:hover {
		color: "rgba(96, 166, 55, 0.5)";
	}

	.modeButton {
		background-color: transparent;
		border: none;
		color: inherit;
		opacity: 0.1;
		position: fixed;
	}

	.modeButton:hover {
		opacity: 0.5;
	}

	.modeButton img {
		width: 3rem;
		height: 3rem;
	}
</style>
