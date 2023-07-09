<script lang="ts">
	import Heading from '$lib/ui/heading.svelte'
	import Posts from '$lib/ui/posts.svelte'

	export let data
</script>

<svelte:head>
	<title>Archive</title>
	<meta content="List of {data.posts.length} posts." name="description" />
</svelte:head>

<Heading>Archive</Heading>

<Posts posts={data.posts}>
	<div slot="title">
		<span class="results">{data.posts.length}</span> results
	</div>
</Posts>

<style>
	.results {
		font-weight: 700;
	}
</style>
