<script>
	export let name;
	export let winner;
	export let total_votes;
	export let dem_count;
	export let dem_pct;
	export let rep_count;
	export let rep_pct;
	import { CheckCircle } from 'lucide-svelte';
</script>

<div id="card">
	{#if winner === 'dem'}
		<div id="dem-header" />
	{:else if winner === 'rep'}
		<div id="rep-header" />
	{/if}
	<section id="card-header">
		<h2>County {name}</h2>
		<!-- <p>Winner: {winner}</p> -->
		<p>Total Votes: {total_votes.toLocaleString()}</p>
	</section>

	<section
		class="candidate-card dem-card"
		style="background-color: {winner === 'dem' ? '#c8eaff' : 'white'}"
	>
		<h3>
			Hillary Clinton
			{#if winner === 'dem'}
				<CheckCircle size={16} color="black" />
			{/if}
		</h3>
		<p>Count: {dem_count.toLocaleString()}</p>
		<p>Percentage: {dem_pct}%</p>
	</section>

	<section
		class="candidate-card rep-card"
		style="background-color: {winner === 'rep' ? '#ffc8c8' : 'white'}"
	>
		<h3>
			Donald Trump
			{#if winner === 'rep'}
				<CheckCircle size={16} color="black" />
			{/if}
		</h3>
		<p>Count: {rep_count.toLocaleString()}</p>
		<p>Percentage: {rep_pct}%</p>
	</section>
</div>

<style>
	#card {
		display: flex;
		flex-direction: column;
		border: 0.5px solid #bcbcbc;
		border-radius: 0.5rem;
		width: 100%;
		padding-bottom: 0.4rem;
	}
	#card-header {
		padding: 0.4rem;
	}

	h3 {
		font-size: 1.5rem;
	}
	p {
		font-size: 1rem;
	}
	.candidate-card {
		padding: 0.4rem;
		border: 0.5px solid #bcbcbc;
	}

	.dem-card {
		border-left: 8px solid #0000ff;
	}

	#dem-header {
		width: 100%;
		height: 8px;
		background-color: #0000ff;
		border-radius: 0.5rem 0.5rem 0 0;
	}

	#rep-header {
		width: 100%;
		height: 8px;
		background-color: #ff0000;
		border-radius: 0.5rem 0.5rem 0 0;
	}

	.rep-card {
		border-left: 8px solid #ff0000;
	}
</style>
