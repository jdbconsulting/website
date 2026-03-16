<script lang="ts">
	interface Props {
		heading?: string;
	}

	let { heading = 'Frequently Asked Questions' }: Props = $props();

	let openIndex = $state<number | null>(null);

	function toggle(index: number) {
		openIndex = openIndex === index ? null : index;
	}

	const items = [
		{
			question: 'What types of companies do you work with?',
			answer:
				'We primarily work with non-military tech companies from early start ups to the largest companies building hardware.'
		},
		{
			question: 'How are engagements typically structured?',
			answer:
				'We can work on both 1) Time & Materials (TM) and 2) Fixed-Price (FP) contracts. Initial consultation is free. A detailed quote can be put together for a small fee.'
		},
		{
			question: 'What does a typical timeline look like?',
			answer:
				'Hardware development projects can range anywhere from a few weeks for the simplest of projects to 6 months for the most complex.'
		},
		{
			question: 'Do you work remote or on-site?',
			answer:
				'While we are based in the San Francisco Bay Area, the majority of our collaborations are remote. Though, on-site visits usuaully occur during bring-up and integration phases.'
		},
		{
			question: 'How do you handle intellectual property?',
			answer:
				'All work product created during an engagement belongs to you. We typically operate under your IP Assignment Agreement or Consulting Agreement, and can offer a Consulting Agreement for your consideration if you would like.'
		}
	];
</script>

<section class="bg-slate-50 py-20 sm:py-28">
	<div class="mx-auto max-w-3xl px-4 sm:px-6 lg:px-8">
		<h2 class="text-center text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
			{heading}
		</h2>
		<div class="mt-12 divide-y divide-slate-200">
			{#each items as item, i}
				<div>
					<button
						class="flex w-full items-center justify-between py-5 text-left transition-colors hover:text-navy-700"
						onclick={() => toggle(i)}
						aria-expanded={openIndex === i}
					>
						<span class="pr-4 text-base font-medium text-slate-900">{item.question}</span>
						<svg
							class="h-5 w-5 shrink-0 text-slate-400 transition-transform duration-200
								{openIndex === i ? 'rotate-180' : ''}"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
							stroke-width="2"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M19.5 8.25l-7.5 7.5-7.5-7.5"
							/>
						</svg>
					</button>
					{#if openIndex === i}
						<div class="pb-5 pr-12">
							<p class="text-sm leading-relaxed text-slate-600">{item.answer}</p>
						</div>
					{/if}
				</div>
			{/each}
		</div>
	</div>
</section>
