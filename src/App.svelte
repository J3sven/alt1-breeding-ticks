<script>
	import Clock from './Clock.svelte';
	export let newUser = true;

	function setCookie(name,value,days) {
		let expires = "";
		if (days) {
			let date = new Date();
			date.setTime(date.getTime() + (days*24*60*60*1000));
			expires = "; expires=" + date.toUTCString();
		}
		document.cookie = name + "=" + (value || "")  + expires + "; path=/";
	}
	function getCookie(name) {
		let nameEQ = name + "=";
		let ca = document.cookie.split(';');
		for(let i=0;i < ca.length;i++) {
			let c = ca[i];
			while (c.charAt(0)==' ') c = c.substring(1,c.length);
			if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
		}
		return null;
	}

	let settingsCookie = getCookie('settings');

	let settings = [{text: 'Chickens', status: true, class: 'path', show: true},
					{text: 'Cows', status: false, show: true},
					{text: 'Jadinkos', status: false, show: true}];

	if(settingsCookie){
		newUser = false;
		console.log('Settings loaded');
	}else{
		setCookie('settings', JSON.stringify(settings), 9999);
	}

	function getColorFromString(color){
		var checkForHex = /(^#[0-9A-F]{6}$)|(^#[0-9A-F]{3}$)/i.test(color);
		
		if(checkForHex)
			return color.substring(1);

		return false;
	}

	function initAlt1(){
		a1lib.identifyUrl("appconfig.json");
	}

	var wh = alt1.rsHeight;
	var ww = alt1.rsWidth;
	var textSize = 30;
	var x = (wh - textSize) - (textSize+800);
	var y = parseInt((ww/2) - ((17*textSize)/2));
	var timeToShow = 10000;

	function leaveTextAlert(){
		alt1.showNotification('Breeding Tick', 'A breeding tick is about to occur! Make sure you leave your farm!', null);
        var color = getColorFromString('#cc0000');
        alt1.overLayText('LEAVE YOUR FARM', parseInt('0xFF' + color), textSize, y, x, timeToShow);
	}

	function enterTextAlert(){
		alt1.showNotification('Breeding Tick', 'A breeding tick now happening! Make sure you enter your farm within the next minute!', null);
        var color = getColorFromString('#6de738');
        alt1.overLayText('ENTER YOUR FARM', parseInt('0xFF' + color), textSize, y, x, timeToShow);
	}
</script>

<svelte:head>
	<script src="alt1lib.js" on:load={initAlt1}></script>
</svelte:head>

<main>

	{#if newUser}
		<h2>Welcome!</h2>
		<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Vel cumque eligendi quis. Reprehenderit labore harum beatae aut ab veritatis saepe soluta, vitae laboriosam quidem doloribus iste voluptatem magni asperiores. Molestias.</p>
	{:else}
		<div class="head">
			<h3>Breeding ticks {newUser}</h3>
		</div>
		<button on:click|once={leaveTextAlert}>
			Leave farm
		</button>
		<button on:click|once={enterTextAlert}>
			Enter farm
		</button>
		<Clock />
	{/if}


	
</main>

<style>
	main {
		padding: 0;
		margin: 0;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.head{
		display: flex;
		width: 100%;
		justify-content: center;
	}
</style>