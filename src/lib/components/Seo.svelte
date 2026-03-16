<script lang="ts">
	interface Props {
		title?: string;
		description?: string;
		ogImage?: string;
	}

	const SITE_NAME = 'JD Brinton Consulting';
	const DEFAULT_DESCRIPTION =
		'Senior electrical engineering consulting for startups and deep-tech teams. Strategy, architecture, and technical execution.';

	let { title = '', description = DEFAULT_DESCRIPTION, ogImage = '' }: Props = $props();

	const fullTitle = $derived(
		title
			? `${title} | ${SITE_NAME}`
			: `${SITE_NAME} — Engineering Leadership for Ambitious Teams`
	);
</script>

<svelte:head>
	<title>{fullTitle}</title>
	<meta name="description" content={description} />
	<meta property="og:title" content={fullTitle} />
	<meta property="og:description" content={description} />
	{#if ogImage}
		<meta property="og:image" content={ogImage} />
	{/if}
	<meta property="og:type" content="website" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={fullTitle} />
	<meta name="twitter:description" content={description} />
</svelte:head>
