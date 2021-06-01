<script>
	import Main from './Main.svelte';
</script>

<main>
	
	<div class="im">
		
	</div>
	<div class='top'>
		<div class='logo'>
			<img class='main-logo' src='/image/Svelte_Logo.png' alt="" width=53 height=64>
		</div>
	</div>
	<Main></Main>
	
	
</main>


<style>

	.main-logo{
		margin: auto;
	}

	main{
		width: 100%;
		height: 100%;
		margin: auto;
		display: flex;
		align-items: center;
	}

	.top{
		position: absolute;
		top: 0;
		display: flex;
		margin-left: auto;
		margin-right: auto;
		width: 100%;
		justify-content: center;
	}

	.logo{
		width: 110px;
		height: 93px;
		background-color: #181818;
		border-radius: 8px;
		display: flex;
		justify-content: center;
		align-content: center;
	}

	.im{
		background: url('/image/image1.png') no-repeat center center fixed;
		background-size: cover;
		opacity: .3;
		width: 100%;
		height: 100%;
		position: fixed;
		z-index: -1;
	}
</style>