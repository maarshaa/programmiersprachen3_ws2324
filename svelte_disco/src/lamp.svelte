<script>
    export let left;
    export let top;
    let color= 'rgb(${Math.random() * 255}, ${Math.random() * 255}, ${Math.random() * 255})';
</script>

<div class="lamp" style="background-color: {color}; left:{left}px; top:{top}px"></div>

<style>
    .lamp {
        position:absolute;
        width: 10px;
        height: 10px;
        border-radius: 50%;
    }
</style>