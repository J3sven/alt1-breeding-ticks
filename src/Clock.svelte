<script>
    import { onMount } from 'svelte';

    let date = new Date();

    function lowerThanTen(number){
        if(number < 10){
            return '0';
        }else{
            return ' ';
        }
    }

    $: hour = date.getHours();
    $: zeroHour = lowerThanTen(date.getHours());
    $: min = date.getMinutes()
    $: zeroMin = lowerThanTen(date.getMinutes());
    $: sec = date.getSeconds();
    $: zeroSec = lowerThanTen(date.getSeconds());

    onMount( () => {
        const interval = setInterval(() => {
            date = new Date();
        }, 200);
    });
</script>

<div class="clock"> 
    {zeroHour}{hour} : {zeroMin}{min} : {zeroSec}{sec}
</div>

<style>

    .clock{
        background: rgba(0, 0, 0, 0.365);
        width: 100%;
        height: 25px;
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
    }

</style>