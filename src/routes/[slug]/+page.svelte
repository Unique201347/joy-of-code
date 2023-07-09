<script lang="ts">
	import { formatDate } from '$lib/utils'
	import * as config from '$lib/site/config'

	import Clipboard from './clipboard.svelte'
	import Overlay from './overlay.svelte'
	import TableOfContents from './toc.svelte'

	export let data

	const { content, frontmatter } = data.post

	let image = `${config.postImage}${encodeURIComponent(frontmatter.title)}.png`
</script>

<svelte:head>
	<title>{frontmatter.title}</title>

	<meta content={frontmatter.description} name="description" />

	<meta content={frontmatter.title} property="og:title" />
	<meta content={image} property="og:image" />
	<meta content={config.siteUrl} property="og:url" />
	<meta content={frontmatter.description} property="og:description" />
	<meta content={config.siteName} property="og:site_name" />
</svelte:head>

<Clipboard />

<main>
	<Overlay />
	<TableOfContents />

	<article class="prose">
		<header>
			<h1>{frontmatter.title}</h1>
			<p>Published {formatDate(frontmatter.published)}</p>
		</header>

		{@html content}
	</article>
</main>
