<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import ContactForm from '$lib/components/ContactForm.svelte';
	import Faq from '$lib/components/Faq.svelte';
</script>

<Seo
	title="Contact"
	description="Get in touch with JD Brinton Consulting. We'd love to discuss your technical challenges and how senior engineering leadership can help."
/>

<Hero
	title="Let's Talk"
	subtitle="Whether you're exploring options or ready to kick off a project, we're here to help. Initial consultations are always complimentary."
	compact
/>

<ContactForm />

<Faq />
