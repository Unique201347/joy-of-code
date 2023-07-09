<script lang="ts">
	import { fade } from 'svelte/transition'
	import type { Post } from '$lib/types'

	export let posts: Post[]
</script>

<section>
	<slot name="title" />

	<div class="cards">
		{#each posts as post, i}
			<div
				in:fade={{
					duration: 300,
					delay: i < 4 ? 100 * i : 100 * 4,
				}}
			>
				<a href="/{post.slug}">
					<article class="card">
						<div class="details">
							<span class="title">{post.title}</span>
							<p class="description">{post.description}</p>
						</div>
					</article>
				</a>
			</div>
		{/each}
	</div>

	<slot name="see-more" />
</section>

<style>
	section {
		margin-top: var(--spacing-32);
		margin-bottom: var(--spacing-16);
	}

	.cards {
		display: grid;
		gap: var(--spacing-24);
		grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
		margin-top: var(--spacing-32);
	}

	.cards a {
		display: block;
		color: inherit;
		font-weight: inherit;
		text-decoration: none;
		transition: color 0.3s ease;
	}

	.cards a::before {
		content: none;
	}

	.card {
		height: 280px;
		display: grid;
		grid-template-rows: min-content;
		padding: var(--spacing-16);
		background-image: var(--clr-card-bg);
		border-top: 1px solid var(--clr-menu-border);
		border-left: 1px solid var(--clr-menu-border);
		border-radius: var(--rounded-20);
		box-shadow: var(--shadow-sm);
		transition: transform 0.2s ease-in-out, box-shadow 0.3s ease,
			outline 0.1s ease;
		transform: translateZ(0);
	}

	.card:hover {
		box-shadow: var(--shadow-md), 0 0 0 2px whitesmoke;
	}

	.card .details {
		align-self: end;
	}

	.card .title {
		font-family: var(font-sans);
		font-size: var(--font-24);
		font-weight: 700;
		line-height: 48px;
		text-transform: capitalize;
	}

	html[data-font='dyslexic'] .card .title {
		font-family: var(--font-dyslexic);
		font-size: var(--font-24);
		line-height: 32px;
	}

	.card .description {
		margin-top: var(--spacing-8);
		font-size: var(--font-16);
		color: var(--clr-card-txt);
	}

	:global([slot='see-more']) {
		width: max-content;
		display: flex;
		gap: var(--spacing-16);
		margin-top: var(--spacing-32);
	}
</style>
