<script>
	export let dino;
	export let currentDinosaur;
	export let correct;
	export let clicked = "none";
	const imagePath = `/images/${dino.name}.png`;
</script>

<button
	class="card-image"
	style=" border-color: {dino === currentDinosaur && correct
		? 'rgb(30, 255, 0)'
		: clicked}"
	on:click={() => {
		clicked = "red";
	}}
	on:mouseleave={() => {
		clicked = "rgba(0, 0, 0, 0)";
	}}
>
	<img src={imagePath} alt="Image of a {dino.name}" />
</button>

<style>
	.card-image {
		border: 10px solid rgba(0, 0, 0, 0);
		background-color: transparent;
		border-radius: 20px;
		height: 100%;
		width: 100%;
		min-width: 12rem;
		max-width: 20rem;
		justify-content: center;
	}

	.card-image:hover {
		transform: scale(1.05);
		transition: transform 0.3s ease;
		cursor: pointer;
	}

	.card-image img {
		width: 102%;
		height: auto;
		object-fit: cover;
		border-radius: 10px;
	}

	@media (max-width: 100rem) {
		.card-image {
			width: 140%;
			height: 100%;
			align-items: center;
		}

		.card-image img {
			width: flex;
			height: 100%;
			object-fit: cover;
			border-radius: 10px;
		}
	}
</style>
