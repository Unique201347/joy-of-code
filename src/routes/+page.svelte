<script lang="ts">
	import { ArrowNarrowRightIcon } from '@rgossiaux/svelte-heroicons/outline'

	import Posts from '$lib/ui/posts.svelte'
	import * as config from '$lib/site/config'

	export let data

	const { posts } = data
</script>

<svelte:head>
	<title>{config.siteTitle}</title>

	<meta content={config.siteDescription} name="description" />

	<meta content={config.siteTitle} property="og:title" />
	<meta content={config.siteImage} property="og:image" />
	<meta content={config.siteUrl} property="og:url" />
	<meta content={config.siteDescription} property="og:description" />
	<meta content={config.siteName} property="og:site_name" />
</svelte:head>

<main>
	<Posts {posts}>
		<a slot="see-more" href="/archive" style="margin-bottom: 20px;">
			<span>See more posts</span>
			<ArrowNarrowRightIcon width="24" height="24" aria-hidden="true" />
		</a>
	</Posts>
</main>
