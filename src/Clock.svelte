<script>
    import { onMount } from 'svelte';

    let date = new Date();
    $: hour = date.getHours() + 2;
    $: min = date.getMinutes();
    $: sec = date.getSeconds();

    onMount( () => {
    const interval = setInterval(() => {
        date = new Date();
    }, 1000);
    });
</script>

<div class="clock"> 
    {hour} : {min} : {sec}
</div>

<style>

    .clock{
        background: rgba(0, 0, 0, 0.665);
        width: 100%;
        height: 20px;
        color: white;
    }

</style>