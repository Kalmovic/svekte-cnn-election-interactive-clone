<script>
	import { setContext } from 'svelte';
	import { writable } from 'svelte/store';
	let countyData = {
		name: '',
		winner: '',
		total_votes: '',
		dem_count: '',
		dem_pct: '',
		rep_count: '',
		rep_pct: ''
	};

	let countyInfo = writable(countyData);

	$: countyInfo.set(countyData);

	setContext('countyData', countyInfo);
</script>

<slot />
