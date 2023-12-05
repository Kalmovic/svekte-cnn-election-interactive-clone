<script lang="ts">
	export let img: string;
	export let description: string;
</script>

<div class="option-card" role="button" tabindex="0">
	<figure>
		<img class="image" src={img} alt={description} />
		<figcaption class="description">{description}</figcaption>
	</figure>
</div>

<style>
	.option-card {
		display: flex;
		flex-direction: column;
		text-align: start;
		padding-bottom: 0.4rem;
		border: 0.5px solid #bcbcbc;
		border-radius: 0.5rem;
	}

	.image {
		width: 300px;
		height: 180px;
		object-fit: cover;
		border-top-right-radius: 0.5rem;
		border-top-left-radius: 0.5rem;
	}

	.image:hover {
		opacity: 0.7;
	}

	figcaption {
		margin-left: 5px;
	}
</style>
