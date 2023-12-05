<script>
	import OptionCard from '../components/option-card.svelte';
	import result2020 from '$lib/assets/2020_results.png';
	import result2024 from '$lib/assets/2024_results.jpg';
</script>

<h1>Results and maps</h1>

<section>
	<a href="/results/2020">
		<OptionCard description="Check the results of the 2020 election." img={result2020} />
	</a>
	<a href="/road-to-270">
		<OptionCard description="Predict the next POTUS!" img={result2024} />
	</a>
</section>

<style>
	h1 {
		font-family: Arial, Helvetica, sans-serif;
		margin: 0;
		width: 100%;
		text-align: left;
		height: fit-content;
		padding-bottom: 1rem;
		display: flex;
		font-size: 2rem; /* Adjust the font size as needed */
		font-weight: bold;
	}

	section {
		display: flex;
		gap: 5rem;
	}

	a {
		text-decoration: none;
		color: inherit;
	}
</style>
