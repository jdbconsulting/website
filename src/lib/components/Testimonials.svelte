<script lang="ts">
	const testimonials = [
		{
			quote:
				'JD Brinton helped us go from concept to working prototype in under 12 weeks. Their senior engineers embedded seamlessly with our team and brought clarity to every technical decision.',
			name: 'Sarah Chen',
			role: 'CTO',
			company: 'Quantum Dynamics'
		},
		{
			quote:
				"The technical due diligence JD Brinton provided was instrumental in our Series B. Their depth of analysis gave our investors the confidence they needed to move forward.",
			name: 'Marcus Rivera',
			role: 'CEO',
			company: 'Helios Robotics'
		},
		{
			quote:
				"We brought JD Brinton in to redesign our power management architecture. They didn't just deliver a better design — they upskilled our entire hardware team in the process.",
			name: 'Dr. Anika Patel',
			role: 'VP Engineering',
			company: 'NovaTech'
		}
	];
</script>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-2xl text-center">
			<h2 class="text-3xl font-bold tracking-tight text-slate-900 sm:text-4xl">
				What Our Clients Say
			</h2>
		</div>
		<div class="mt-16 grid gap-8 lg:grid-cols-3">
			{#each testimonials as t}
				<blockquote
					class="flex flex-col justify-between rounded-2xl border border-slate-200 bg-white p-8"
				>
					<p class="text-sm leading-relaxed text-slate-700">"{t.quote}"</p>
					<footer class="mt-6 flex items-center gap-3">
						<div
							class="flex h-10 w-10 items-center justify-center rounded-full bg-navy-100 text-sm font-bold text-navy-700"
						>
							{t.name
								.split(' ')
								.map((n) => n[0])
								.join('')}
						</div>
						<div>
							<div class="text-sm font-semibold text-slate-900">{t.name}</div>
							<div class="text-xs text-slate-500">{t.role}, {t.company}</div>
						</div>
					</footer>
				</blockquote>
			{/each}
		</div>
	</div>
</section>
