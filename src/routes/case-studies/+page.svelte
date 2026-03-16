<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import CaseStudyCards from '$lib/components/CaseStudyCards.svelte';
	import Cta from '$lib/components/Cta.svelte';
</script>

<Seo
	title="Case Studies"
	description="See how JD Brinton Consulting has helped startups and deep-tech companies solve complex technical challenges and ship exceptional products."
/>

<Hero
	title="Proven Results, Real Impact"
	subtitle="We measure success by the outcomes our clients achieve. Here's a selection of the work we're most proud of."
	primaryCta="Start Your Project"
	primaryHref="/contact"
	compact
/>

<CaseStudyCards />

<section class="border-t border-slate-100 bg-slate-50 py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">Industries We Serve</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-600">
				Deep technical expertise across the industries where hardware and software meet.
			</p>
		</div>
		<div class="mt-16 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
			{#each [
				{
					title: 'High Performance Computing',
					description: 'Custom accelerators and FPGA-based inference hardware.',
					icon: 'M8.25 3v1.5M4.5 8.25H3m18 0h-1.5M4.5 12H3m18 0h-1.5m-15 3.75H3m18 0h-1.5M8.25 19.5V21M12 3v1.5m0 15V21m3.75-18v1.5m0 15V21m-9-1.5h10.5a2.25 2.25 0 002.25-2.25V6.75a2.25 2.25 0 00-2.25-2.25H6.75A2.25 2.25 0 004.5 6.75v10.5a2.25 2.25 0 002.25 2.25zm.75-12h9v9h-9v-9z'
				},
				{
					title: 'Commercial Aerospace',
					description: 'Avionics, launch vehicles, satellites, and UAV systems.',
					icon: 'M15.59 14.37a6 6 0 01-5.84 7.38v-4.8m5.84-2.58a14.98 14.98 0 006.16-12.12A14.98 14.98 0 009.631 8.41m5.96 5.96a14.926 14.926 0 01-5.841 2.58m-.119-8.54a6 6 0 00-7.381 5.84h4.8m2.58-5.84a14.927 14.927 0 00-2.58 5.84m2.699 2.7c-.103.021-.207.041-.311.06a15.09 15.09 0 01-2.448-2.448 14.9 14.9 0 01.06-.312m-2.24 2.39a4.493 4.493 0 00-1.757 4.306 4.493 4.493 0 004.306-1.758M16.5 9a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z'
				},
				{
					title: 'Scientific Instrumentation',
					description: 'Electron microscopy, precision sensing, and lab equipment.',
					icon: 'M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5m14.8.8l1.402 1.402c1.232 1.232.65 3.318-1.067 3.611A48.309 48.309 0 0112 21c-2.773 0-5.491-.235-8.135-.687-1.718-.293-2.3-2.379-1.067-3.61L5 14.5'
				},
				{
					title: 'IoT & Remote Sensing',
					description: 'Ultra-low-power embedded platforms with cellular and satellite backhaul.',
					icon: 'M9.348 14.652a3.75 3.75 0 010-5.304m5.304 0a3.75 3.75 0 010 5.304m-7.425 2.121a6.75 6.75 0 010-9.546m9.546 0a6.75 6.75 0 010 9.546M5.106 18.894c-3.808-3.807-3.808-9.98 0-13.788m13.788 0c3.808 3.807 3.808 9.98 0 13.788M12 12h.008v.008H12V12zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z'
				},
				{
					title: 'Telecom & Wireless',
					description: 'RF hardware, custom filters, and broadband infrastructure.',
					icon: 'M3 7.5L7.5 3m0 0L12 7.5M7.5 3v13.5m13.5 0L16.5 21m0 0L12 16.5m4.5 4.5V7.5'
				},
				{
					title: 'Consumer Electronics',
					description: 'Rapid prototyping from concept through production.',
					icon: 'M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3'
				}
			] as industry}
				<div class="rounded-2xl border border-slate-200 bg-white p-6 transition-all hover:border-slate-300 hover:shadow-lg">
					<div class="flex h-12 w-12 items-center justify-center rounded-xl bg-navy-50">
						<svg
							class="h-6 w-6 text-navy-600"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
							stroke-width="1.5"
							aria-hidden="true"
						>
							<path stroke-linecap="round" stroke-linejoin="round" d={industry.icon} />
						</svg>
					</div>
					<h3 class="mt-4 text-base font-semibold text-slate-900">{industry.title}</h3>
					<p class="mt-2 text-sm leading-relaxed text-slate-600">{industry.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<Cta
	heading="Have a Similar Challenge?"
	body="Let's talk about how our experience can accelerate your project."
	buttonText="Get in Touch"
/>
