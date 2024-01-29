<script>
	import App from "./App.svelte";

	let darkMode = true;

	function toggleDarkMode() {
		darkMode = !darkMode;
	}
</script>

<div id="wrapper" class={darkMode ? "dark-mode" : ""}>
	<button class="modeButton" on:click={toggleDarkMode}>
		{#if darkMode}
			<img src="images/sun.png" alt="Light Mode" />
		{:else}
			<img src="images/moondunkel.png" alt="Dark Mode" />
		{/if}
	</button>
	<App {darkMode}></App>
</div>
