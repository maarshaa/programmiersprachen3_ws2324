<script>
    export let left;
    export let top;
    export let size; // new property for lamp size

    let interval = Math.random() * 1000 + 100;

    let color = `rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255})`;

    let isShining = true;

    function toggleLamp() {
        isShining = !isShining;
    }

    setInterval(toggleLamp, interval);
</script>

<div class="lamp" class:hidden={!isShining} style="background-color: {color}; left: {left}px; top: {top}px; width: {size}px; height: {size}px;"></div>

<style>
    .lamp {
        position: absolute;
        border-radius: 50%;
    }
    .hidden {
        opacity: 0;
        transition: all 0.5s ease-in-out;
    }
</style>