<script>
	let selectedState = '';

	const states = [
		'Alabama',
		'Alaska',
		'Arizona',
		'Arkansas',
		'California'
		// ... add more states here
	];

	function handleChange(event) {
		selectedState = event.target.value;
	}
</script>

<select value={selectedState} on:change={(e) => handleChange(e)}>
	{#each states as state}
		<option value={state}>{state}</option>
	{/each}
</select>

<p>Selected state: {selectedState}</p>
