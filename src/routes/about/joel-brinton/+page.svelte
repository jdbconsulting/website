<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Timeline from '$lib/components/Timeline.svelte';
	import ValueProps from '$lib/components/ValueProps.svelte';
	import Cta from '$lib/components/Cta.svelte';
</script>

<Seo
	title="Joel Brinton"
	description="Meet JD Brinton — founder and principal engineer at JDBC with two decades of experience from rockets to electron microscopes to wireless broadband."
/>

<section class="relative overflow-hidden bg-navy-950">
	<div
		class="absolute inset-0 bg-[radial-gradient(ellipse_at_top_right,rgba(59,130,246,0.12),transparent_60%)]"
		aria-hidden="true"
	></div>
	<div class="relative mx-auto max-w-7xl px-4 py-16 sm:px-6 sm:py-20 lg:px-8 lg:py-24">
		<a
			href="/about"
			class="inline-flex items-center gap-1.5 text-sm font-medium text-slate-400 transition-colors hover:text-white"
		>
			<svg
				class="h-4 w-4"
				fill="none"
				viewBox="0 0 24 24"
				stroke="currentColor"
				stroke-width="2"
				aria-hidden="true"
			>
				<path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18" />
			</svg>
			About JDBC
		</a>
		<h1 class="mt-6 max-w-4xl text-4xl font-bold tracking-tight text-white sm:text-5xl">
			JD Brinton
		</h1>
		<p class="mt-2 text-lg font-medium text-accent-400">Founder & Principal Engineer</p>
	</div>
</section>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="grid items-center gap-12 lg:grid-cols-2 lg:gap-20">
			<div class="mx-auto max-w-lg lg:mx-0">
				<img
					src="/images/headshot2.jpg"
					alt="JD Brinton, Founder and Principal Engineer"
					class="aspect-4/5 w-full rounded-2xl object-cover shadow-lg"
					width="640"
					height="800"
				/>
			</div>
			<div>
				<div class="space-y-5 text-base leading-relaxed text-slate-600">
					<p>
						With over two decades of experience in electrical engineering and embedded
						software development I have worked on everything from ultra-low power
						electronics (Femtowatts) to ultra-high powered electronics (Megawatts).
						I've done digital design, embedded programming, custom Linux distros, and
						even programmed PLCs and CLPDs.
						On the hardware side, I've designed hundreds of PCBs from concept to
						schematic to layout, production, and testing. I've done custom RF hardware
						including discrete filters, mixers and amplifiers.
					</p>
					<p>
						I enjoy working on ambitious projects that push the boundaries of
						engineering. I've designed my own hardware as well as lead small technical
						teams though complex requirements.
					</p>
					<p>
						JDBC exists to help ambitious teams get a solid start on their highly
						technical challenges. We can take a concept and rapidly turn it into
						a working proof-of-concept (POC).
					</p>
				</div>
				<div class="mt-8 flex items-center gap-4">
					<a
						href="https://www.linkedin.com/in/joeldbrinton/"
						target="_blank"
						rel="noopener noreferrer"
						class="inline-flex items-center gap-2 rounded-lg bg-[#0A66C2] px-4 py-2.5 text-sm font-medium text-white transition-opacity hover:opacity-90"
					>
						<svg class="h-5 w-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
							<path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
						</svg>
						LinkedIn
					</a>
				</div>
			</div>
		</div>
	</div>
</section>

<Timeline />

<ValueProps
	heading="My Principles"
	subheading="These guide how I work and the outcomes I commit to."
/>

<Cta />
