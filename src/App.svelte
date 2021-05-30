
<script>
	import Main from './Main.svelte';
</script>

<main>
	
	<div class="im">
		
	</div>
	<Main></Main>
	
	
</main>


<style>
	main{
		width: 100%;
		height: 100%;
		margin: auto;
		display: flex;
		align-items: center;
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