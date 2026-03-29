<script lang="ts">
	import Seo from '$lib/components/Seo.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import Cta from '$lib/components/Cta.svelte';
</script>

<Seo
	title="About"
	description="JD Brinton Consulting helps startups and deep-tech companies tackle their hardest engineering challenges — from concept to working hardware."
/>

<Hero
	title="Engineering That Ships"
	subtitle="JD Brinton Consulting was founded to help ambitious teams get a solid start on their most complex technical challenges. We take concepts and rapidly turn them into working proof-of-concepts."
	compact
/>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-3xl">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
				Who We Are
			</h2>
			<div class="mt-6 space-y-5 text-base leading-relaxed text-slate-600">
				<p>
					JDBC (JD Brinton Consulting, Inc.) is a computer and electrical engineering consulting firm based in California. Our mission is to help your team rapidly build sophisticated hardware proof of concepts.
				</p>
			</div>
		</div>
	</div>
</section>

<section class="border-t border-slate-100 bg-slate-50 py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-3xl">
			<a
				href="/about/history"
				class="group flex items-start gap-5 rounded-2xl border border-slate-200 bg-white p-6 transition-all hover:border-accent-300 hover:shadow-lg sm:items-center sm:p-8"
			>
				<div class="flex h-12 w-12 shrink-0 items-center justify-center rounded-xl bg-navy-950 text-accent-400">
					<svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
						<path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
					</svg>
				</div>
				<div class="flex-1">
					<h3 class="text-lg font-semibold text-slate-900 group-hover:text-navy-700">Our History</h3>
					<p class="mt-1 text-sm leading-relaxed text-slate-600">
						From Brinton Research in 2009 through Signal Labs, Amaya Tech, and Electron Labs — the full lineage of how JDBC came to be.
					</p>
				</div>
				<svg
					class="mt-1 h-5 w-5 shrink-0 text-slate-300 transition-transform group-hover:translate-x-0.5 group-hover:text-accent-500"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
					aria-hidden="true"
				>
					<path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
				</svg>
			</a>
		</div>
	</div>
</section>

<section class="border-t border-slate-100 bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">Our Team</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-600">
				Led by an engineer with two decades across aerospace, telecom, and consumer electronics.
			</p>
		</div>
		<div class="mx-auto mt-12 max-w-sm">
			<a
				href="/about/joel-brinton"
				class="group block overflow-hidden rounded-2xl border border-slate-200 bg-white transition-all hover:border-accent-300 hover:shadow-lg"
			>
				<div class="aspect-4/3 overflow-hidden">
					<img
						src="/images/headshot2.jpg"
						alt="JD Brinton"
						class="h-full w-full object-cover object-top transition-transform duration-300 group-hover:scale-105"
						width="640"
						height="480"
					/>
				</div>
				<div class="p-6">
					<h3 class="text-lg font-semibold text-slate-900 group-hover:text-navy-700">
						JD Brinton
					</h3>
					<p class="mt-1 text-sm font-medium text-slate-500">Founder & Principal Engineer</p>
					<p class="mt-3 text-sm leading-relaxed text-slate-600">
						Two decades of experience from rockets to electron microscopes to wireless broadband.
						SpaceX, XCOR Aerospace, Google ATAP, Relativity Space.
					</p>
					<span
						class="mt-4 inline-flex items-center gap-1 text-sm font-medium text-accent-600 group-hover:text-accent-500"
					>
						View full bio
						<svg
							class="h-4 w-4 transition-transform group-hover:translate-x-0.5"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
							stroke-width="2"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"
							/>
						</svg>
					</span>
				</div>
			</a>
		</div>
	</div>
</section>

<section class="border-t border-slate-100 bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-3xl">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
				Return &amp; Refund Policy
			</h2>
			<div class="mt-6 space-y-5 text-base leading-relaxed text-slate-600">
				<p>
					All consulting services provided by JD Brinton Consulting, Inc. are non-refundable.
					Due to the nature of professional engineering services — including time, expertise, and
					intellectual property delivered — all fees are final upon payment.
				</p>
				<p>
					No returns, refunds, or credits will be issued for completed work, work in progress,
					or prepaid retainer balances. By engaging our services, clients acknowledge and agree
					to this policy.
				</p>
				<p>
					If you have questions or concerns about a specific engagement, please
					<a href="/contact" class="font-medium text-navy-700 underline decoration-navy-300 transition-colors hover:text-accent-600 hover:decoration-accent-400">contact us</a>
					directly to discuss.
				</p>
			</div>
		</div>
	</div>
</section>

<Cta />
