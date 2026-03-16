<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import LogoCloud from '$lib/components/LogoCloud.svelte';
	import ServicesGrid from '$lib/components/ServicesGrid.svelte';
	import ValueProps from '$lib/components/ValueProps.svelte';
	import ProjectGallery from '$lib/components/ProjectGallery.svelte';
	import Cta from '$lib/components/Cta.svelte';
</script>

<Seo />

<Hero
	title="Human Hardware Engineering Leadership in the Age of AI"
	subtitle="We partner with highly technical hardware companies to rapidly build proof-of-concepts."
	primaryCta="Start a Conversation"
	primaryHref="/contact"
	secondaryCta="View Case Studies"
	secondaryHref="/case-studies"
	backgroundImage="/images/hero-bg.jpg"
/>

<LogoCloud />

<ServicesGrid />

<ValueProps />

<ProjectGallery />

<Cta backgroundImage="/images/cta-bg.jpg" />
