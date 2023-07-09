<script lang="ts">
	import { page } from '$app/stores'
	import * as config from '$lib/site/config'

	import Heading from '$lib/ui/heading.svelte'
	import Posts from '$lib/ui/posts.svelte'

	export let data

	const { posts } = data
	const category = $page.params.category
</script>

<svelte:head>
	<title>{config.categories[category]}</title>
	<meta content="{config.categories[category]} category." name="description" />
</svelte:head>

<Heading>{config.categories[category]}</Heading>

<Posts {posts}>
	<div slot="title">
		<span>{posts.length}</span> results
	</div>
</Posts>
