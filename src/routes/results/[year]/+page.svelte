<script>
	import mapboxgl from 'mapbox-gl';
	import { goto } from '$app/navigation';
	import { page } from '$app/stores';
	import { getContext } from 'svelte';

	const states = getContext('states');
	let map;
	let selectedState = '';

	function initMap(container) {
		map = new mapboxgl.Map({
			container: container,
			style: 'mapbox://styles/kalmovic/clprq3i3d00oi01p47kmh7fzo',
			center: [-98.5917, 38.6699],
			zoom: 3,
			accessToken:
				'pk.eyJ1Ijoia2FsbW92aWMiLCJhIjoiY2xwZDBndmxpMDRmODJqcDZmdXVwbjVodCJ9.JI6tm3QmcOtby0Oao7i9og'
		});

		map.on('load', () => {
			// Hover interaction for clusters
			map.on('click', 'historical-pres-elections-state', (e) => {
				console.log('hovering');
				console.log(e.features);
				goto(`/results/${$page.params.year}/${e.features[0].properties.state_abbrev}`);
			});

			map.on('mouseenter', 'historical-pres-elections-state', () => {
				map.getCanvas().style.cursor = 'pointer';
			});
		});
	}
	function handleSelectState(event) {
		goto(`/results/${$page.params.year}/${event.target.value}`);
	}
</script>

<section class="state-selector">
	<h1>Select a state</h1>
	<select value={selectedState} on:change={handleSelectState} placeholder="Alabama">
		{#each $states as { state, name }}
			<option value={state}>
				{name}
			</option>
		{/each}
	</select>
</section>

<section class="map-legend">
	<div class="legend-item">
		<div class="legend-aquare dem-color" />
		<p>Democrat</p>
	</div>
	<div class="legend-item">
		<div class="legend-aquare rep-color" />
		<p>Republican</p>
	</div>
</section>

<div id="map" use:initMap></div>

<style>
	#map {
		width: 100%;
		height: 400px;
	}

	.state-selector {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: center;
		margin-bottom: 20px;
		max-width: fit-content;
	}
	select {
		padding: 10px;
		font-size: 16px;
		border: 1px solid #bcbcbc;
		border-radius: 5px;
		background-color: #ffffff;
		color: #000000;
		gap: 10px;
		width: 100%;
	}

	option {
		text-transform: capitalize;
		background-color: white;
	}

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

	.map-legend {
		display: flex;
		flex-direction: row;
		gap: 20px;
		padding: 2rem 0 0.5rem;
	}

	.legend-item {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		gap: 10px;
	}

	.legend-aquare {
		width: 12px;
		height: 12px;
	}

	.dem-color {
		background-color: #0000ff;
	}

	.rep-color {
		background-color: #ff0000;
	}
</style>
