<script>
	import '../app.css';
	import CNN_Logo from '$lib/assets/cnn_logo.png';
</script>

<header>
	<div class="header-container">
		<a href="/">
			<img src={CNN_Logo} alt="CNN Logo" width="150" />
		</a>
	</div>
</header>
<main>
	<slot />
</main>

<style>
	main {
		margin: 0 auto;
		max-width: 960px;
		padding: 2rem 0;
	}

	header {
		width: 100%;
		border: 0.5px solid #bcbcbc;
	}
	.header-container {
		max-width: 960px;
		margin: 0 auto;
	}
</style>
