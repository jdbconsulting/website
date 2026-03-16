<script lang="ts">
	interface Props {
		heading?: string;
		subheading?: string;
	}

	let {
		heading = 'Why Teams Choose JDBC',
		subheading = 'We bring the rigor of senior hardware engineering leadership for your early proof of concepts.'
	}: Props = $props();

	const values = [
		{
			step: '01',
			title: 'Correct Architecture From Beginning',
			description:
				'The right system or PCB design from the beginning can dramatically reduce the total scope of a project.'
		},
		{
			step: '02',
			title: 'Constantly Remove Complexity',
			description:
				'Its easy for an engineer to throw in a new processor, but how often do you remove one?'
		},
		{
			step: '03',
			title: 'Don\'t Shy Away From Hard Designs',
			description:
				'If its worth doing, its hard.'
		},
		{
			step: '04',
			title: 'Integrated Solutions Can Often Be Less Work',
			description:
				`Using someone\'s prebaked solution can seem attractive, but it often just shifts the complexity from first principles to someone's poor implementation.`
		},
		{
			step: '05',
			title: 'Love The Crunch Times',
			description:
				'No PCB in my career has ever been completed without crunch time. Do what it takes to get a design over the finish line!'
		},
		{
			step: '06',
			title: 'Follow Process',
			description:
				'PCB design is a long-lead time effort. The more process is in place, the fewer mistakes are made.'
		}
	];
</script>

<section class="bg-slate-50 py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">{heading}</h2>
			<p class="mt-4 text-lg leading-relaxed text-slate-600">{subheading}</p>
		</div>
		<div class="mt-16 grid gap-10 sm:grid-cols-2">
			{#each values as value}
				<div class="flex gap-5">
					<span
						class="shrink-0 text-3xl font-bold leading-none tracking-tight text-navy-200"
						aria-hidden="true">{value.step}</span
					>
					<div>
						<h3 class="text-lg font-semibold text-slate-900">{value.title}</h3>
						<p class="mt-2 text-sm leading-relaxed text-slate-600">{value.description}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
