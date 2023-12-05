<script>
	import { setContext } from 'svelte';
	import { writable } from 'svelte/store';

	/** @type {import('./$types').LayoutData} */
	export let usStates = [
		{ state: 'AL', name: 'Alabama', coordinates: [-86.902298, 32.318231] },
		{ state: 'AK', name: 'Alaska', coordinates: [-149.493673, 64.200841] },
		{ state: 'AZ', name: 'Arizona', coordinates: [-111.093731, 34.048927] },
		{ state: 'AR', name: 'Arkansas', coordinates: [-92.302211, 34.746482] },
		{ state: 'CA', name: 'California', coordinates: [-119.538329, 36.778259] },
		{ state: 'CO', name: 'Colorado', coordinates: [-105.782067, 39.550051] },
		{ state: 'CT', name: 'Connecticut', coordinates: [-72.699805, 41.603221] },
		{ state: 'DE', name: 'Delaware', coordinates: [-75.52767, 38.910832] },
		{ state: 'FL', name: 'Florida', coordinates: [-81.515754, 27.994402] },
		{ state: 'GA', name: 'Georgia', coordinates: [-83.42716, 32.678125] },
		{ state: 'HI', name: 'Hawaii', coordinates: [-157.858333, 21.306944] },
		{ state: 'ID', name: 'Idaho', coordinates: [-114.742041, 44.068202] },
		{ state: 'IL', name: 'Illinois', coordinates: [-89.398528, 40.633125] },
		{ state: 'IN', name: 'Indiana', coordinates: [-86.158068, 39.768403] },
		{ state: 'IA', name: 'Iowa', coordinates: [-93.097702, 41.878003] },
		{ state: 'KS', name: 'Kansas', coordinates: [-98.484246, 39.011902] },
		{ state: 'KY', name: 'Kentucky', coordinates: [-84.270018, 37.839333] },
		{ state: 'LA', name: 'Louisiana', coordinates: [-91.962333, 30.984298] },
		{ state: 'ME', name: 'Maine', coordinates: [-69.765261, 45.253783] },
		{ state: 'MD', name: 'Maryland', coordinates: [-76.641273, 39.045753] },
		{ state: 'MA', name: 'Massachusetts', coordinates: [-71.382437, 42.407211] },
		{ state: 'MI', name: 'Michigan', coordinates: [-84.560327, 44.314844] },
		{ state: 'MN', name: 'Minnesota', coordinates: [-93.298279, 46.729553] },
		{ state: 'MS', name: 'Mississippi', coordinates: [-89.398528, 32.354668] },
		{ state: 'MO', name: 'Missouri', coordinates: [-92.329292, 37.964253] },
		{ state: 'MT', name: 'Montana', coordinates: [-110.454353, 46.879682] },
		{ state: 'NE', name: 'Nebraska', coordinates: [-99.901813, 41.492537] },
		{ state: 'NV', name: 'Nevada', coordinates: [-116.419389, 38.80261] },
		{ state: 'NH', name: 'New Hampshire', coordinates: [-71.537451, 42.995639] },
		{ state: 'NJ', name: 'New Jersey', coordinates: [-74.405661, 40.058324] },
		{ state: 'NM', name: 'New Mexico', coordinates: [-105.87009, 34.51994] },
		{ state: 'NY', name: 'New York', coordinates: [-74.005973, 40.712776] },
		{ state: 'NC', name: 'North Carolina', coordinates: [-79.0193, 35.759573] },
		{ state: 'ND', name: 'North Dakota', coordinates: [-99.901813, 47.551493] },
		{ state: 'OH', name: 'Ohio', coordinates: [-82.907123, 40.417287] },
		{ state: 'OK', name: 'Oklahoma', coordinates: [-97.092877, 35.007752] },
		{ state: 'OR', name: 'Oregon', coordinates: [-122.676207, 45.523064] },
		{ state: 'PA', name: 'Pennsylvania', coordinates: [-77.860001, 41.203323] },
		{ state: 'RI', name: 'Rhode Island', coordinates: [-71.477429, 41.580095] },
		{ state: 'SC', name: 'South Carolina', coordinates: [-81.163725, 33.836081] },
		{ state: 'SD', name: 'South Dakota', coordinates: [-99.901813, 43.969515] },
		{ state: 'TN', name: 'Tennessee', coordinates: [-86.580447, 35.517491] },
		{ state: 'TX', name: 'Texas', coordinates: [-99.901813, 31.968599] },
		{ state: 'UT', name: 'Utah', coordinates: [-111.093731, 39.32098] },
		{ state: 'VT', name: 'Vermont', coordinates: [-72.577841, 44.558803] },
		{ state: 'VA', name: 'Virginia', coordinates: [-78.656894, 37.431573] },
		{ state: 'WA', name: 'Washington', coordinates: [-119.487436, 47.751074] },
		{ state: 'WV', name: 'West Virginia', coordinates: [-80.454903, 38.597626] },
		{ state: 'WI', name: 'Wisconsin', coordinates: [-89.398528, 43.78444] },
		{ state: 'WY', name: 'Wyoming', coordinates: [-107.290283, 43.075968] }
	];

	// Create a store and update it when necessary...
	const states = writable();
	$: states.set(usStates);

	// ...and add it to the context for child components to access
	setContext('states', states);
</script>

<slot />
