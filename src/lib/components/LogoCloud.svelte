<script lang="ts">
const companies = [
	'ABL Space Systems',
	'Apollo Fusion (now Astra Space)',
	'Cape (now Motorola)',
	'Fathom Radiant',
	'Google',
	'Halcyon Molecular',
	'Kubicam (now Huddly)',
	'Marble Robotics (now Caterpillar)',
	'Momentus',
	'Movidius (now Intel)',
	'Red Leader Technologies',
	'Reflect Space',
	'Signal Laboratories',
	'Skydio',
	'Spaceflight (now Firefly)',
	'SpaceX',
	'SpaceX',
	'Techniquip',
	'Vantage Robotics',
	'Ventions LLC (now Astra Space)',
	'Verdant Robotics',
	'View',
	'XCOR Aerospace'
];
</script>

<section class="border-y border-slate-100 bg-slate-50/60">
	<div class="mx-auto max-w-7xl px-4 py-12 sm:px-6 lg:px-8">
		<p class="text-center text-xs font-medium uppercase tracking-[0.2em] text-slate-400">
			Trusted by engineering teams at
		</p>
		<div class="mt-8 flex flex-wrap items-center justify-center gap-x-12 gap-y-4">
			{#each companies as company}
				<span class="text-base font-semibold text-slate-300 sm:text-lg">{company}</span>
			{/each}
		</div>
	</div>
</section>
