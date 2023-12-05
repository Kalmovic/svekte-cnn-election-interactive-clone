<script>
	import mapboxgl from 'mapbox-gl';
	import { page } from '$app/stores';
	import { getContext } from 'svelte';
	import CountyResult from '../../../../components/county-result.svelte';

	const states = getContext('states');
	const county = getContext('countyData');
	let map;

	let currentState = $states.find((state) => state.state === $page.params.state);

	function initMap(container) {
		map = new mapboxgl.Map({
			container: container,
			style: 'mapbox://styles/kalmovic/clprq3i3d00oi01p47kmh7fzo',
			center: currentState.coordinates,
			zoom: 5,
			accessToken:
				'pk.eyJ1Ijoia2FsbW92aWMiLCJhIjoiY2xwZDBndmxpMDRmODJqcDZmdXVwbjVodCJ9.JI6tm3QmcOtby0Oao7i9og'
		});

		map.on('load', () => {
			map.on('mousemove', 'historical-pres-elections-county', (e) => {
				map.getCanvas().style.cursor = 'pointer';
				county.set({
					name: e.features[0].properties.name,
					winner: e.features[0].properties['2016_winner'],
					total_votes: e.features[0].properties['2016_total_votes'],
					dem_count: e.features[0].properties['2016_dem_count'],
					dem_pct: e.features[0].properties['2016_dem_pct'],
					rep_count: e.features[0].properties['2016_rep_count'],
					rep_pct: e.features[0].properties['2016_rep_pct']
				});
			});
		});
	}
</script>

<article>
	<header>
		<h1>
			{$page.params.year}
			{currentState.name} counties results
		</h1>
	</header>
	<section>
		<aside>
			<div id="map" use:initMap></div>
		</aside>
		<CountyResult {...$county} />
	</section>
</article>

<style>
	article {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
	header {
		padding: 1.5rem 0;
	}
	h1 {
		margin: 0;
		width: 100%;
		text-align: center;
		border: 1px solid #000; /* Use your desired border color */
		text-transform: uppercase;
		padding: 1rem;
		font-size: 2rem; /* Adjust the font size as needed */
		font-weight: bold;
	}
	section {
		display: flex;
		flex-direction: row;
		align-items: start;
		justify-content: center;
		gap: 1rem;
	}
	aside {
		display: flex;
		flex-direction: column;
		align-items: left;
		justify-content: left;
	}
	#map {
		width: 600px;
		height: 450px;
	}
</style>
