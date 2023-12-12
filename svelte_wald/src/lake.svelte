<script>
    export let left;
    export let top;
    export let size; // new property for lamp size

    let color = `rgb(0, 100, ${Math.random() * 255 +100})`;

</script>

<div class="lake" style="background-color: {color}; left: {left}px; top: {top}px; width: {size}px; height: {size}px;"></div>

<style>
    .lake {
        position: absolute;
        align-items: center;
        border-radius: 35%;
    }
</style>