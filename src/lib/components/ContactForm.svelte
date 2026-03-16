<script lang="ts">
	let status: 'idle' | 'submitting' | 'success' | 'error' = $state('idle');
	let errorMessage = $state('');

	async function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		const form = e.currentTarget as HTMLFormElement;
		status = 'submitting';

		try {
			const res = await fetch('https://formsubmit.co/ajax/hello@jdbrinton.consulting', {
				method: 'POST',
				headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
				body: JSON.stringify(Object.fromEntries(new FormData(form)))
			});

			if (res.ok) {
				status = 'success';
				form.reset();
			} else {
				status = 'error';
				errorMessage = 'Something went wrong. Please try again or email us directly.';
			}
		} catch {
			status = 'error';
			errorMessage = 'Network error. Please check your connection and try again.';
		}
	}
</script>

<section class="bg-white py-20 sm:py-28">
	<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
		<div class="grid gap-16 lg:grid-cols-5">
			<div class="lg:col-span-2">
				<h2 class="text-3xl font-bold tracking-tight text-slate-900">Get in Touch</h2>
				<p class="mt-4 text-base leading-relaxed text-slate-600">
					Whether you have a specific project in mind or want to explore how we can help,
					we'd love to hear from you. Most initial consultations are complimentary.
				</p>

				<dl class="mt-10 space-y-6">
					<div>
						<dt class="text-xs font-semibold uppercase tracking-wider text-slate-400">Email</dt>
						<dd class="mt-1">
							<a
								href="mailto:hello@jdbrinton.consulting"
								class="text-sm font-medium text-slate-900 transition-colors hover:text-accent-600"
								>hello@jdbrinton.consulting</a
							>
						</dd>
					</div>
					<div>
						<dt class="text-xs font-semibold uppercase tracking-wider text-slate-400">Phone</dt>
						<dd class="mt-1 text-sm font-medium text-slate-900">+1 (858) 414-1421</dd>
					</div>
					<div>
						<dt class="text-xs font-semibold uppercase tracking-wider text-slate-400">
							Location
						</dt>
						<dd class="mt-1 text-sm font-medium text-slate-900">Concord, CA</dd>
					</div>
					<div>
						<dt class="text-xs font-semibold uppercase tracking-wider text-slate-400">
							Response Time
						</dt>
						<dd class="mt-1 text-sm font-medium text-slate-900">Within 1 business day</dd>
					</div>
				</dl>
			</div>

			{#if status === 'success'}
				<div class="flex flex-col items-center justify-center text-center lg:col-span-3">
					<div
						class="flex h-16 w-16 items-center justify-center rounded-full bg-green-100"
					>
						<svg
							class="h-8 w-8 text-green-600"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="2"
							stroke="currentColor"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M4.5 12.75l6 6 9-13.5"
							/>
						</svg>
					</div>
					<h3 class="mt-4 text-xl font-semibold text-slate-900">Message Sent</h3>
					<p class="mt-2 text-sm text-slate-600">
						Thank you for reaching out. We'll get back to you within one business day.
					</p>
					<button
						type="button"
						onclick={() => (status = 'idle')}
						class="mt-6 text-sm font-medium text-accent-600 transition-colors hover:text-accent-700"
					>
						Send another message
					</button>
				</div>
			{:else}
				<form
					class="space-y-6 lg:col-span-3"
					onsubmit={handleSubmit}
				>
					<input type="text" name="_honey" class="hidden" />
					<input type="hidden" name="_subject" value="New inquiry from jdbrinton.consulting" />

					<div class="grid gap-6 sm:grid-cols-2">
						<div>
							<label for="name" class="block text-sm font-medium text-slate-700"
								>Full Name</label
							>
							<input
								type="text"
								id="name"
								name="name"
								autocomplete="name"
								required
								class="mt-1.5 block w-full rounded-lg border-slate-300 text-sm shadow-sm transition-colors focus:border-accent-500 focus:ring-accent-500"
								placeholder="Jane Smith"
							/>
						</div>
						<div>
							<label for="email" class="block text-sm font-medium text-slate-700"
								>Email</label
							>
							<input
								type="email"
								id="email"
								name="email"
								autocomplete="email"
								required
								class="mt-1.5 block w-full rounded-lg border-slate-300 text-sm shadow-sm transition-colors focus:border-accent-500 focus:ring-accent-500"
								placeholder="jane@company.com"
							/>
						</div>
					</div>

					<div class="grid gap-6 sm:grid-cols-2">
						<div>
							<label for="company" class="block text-sm font-medium text-slate-700"
								>Company</label
							>
							<input
								type="text"
								id="company"
								name="company"
								autocomplete="organization"
								class="mt-1.5 block w-full rounded-lg border-slate-300 text-sm shadow-sm transition-colors focus:border-accent-500 focus:ring-accent-500"
								placeholder="Acme Corp"
							/>
						</div>
						<div>
							<label for="service" class="block text-sm font-medium text-slate-700"
								>Service Interest</label
							>
							<select
								id="service"
								name="service"
								class="mt-1.5 block w-full rounded-lg border-slate-300 text-sm shadow-sm transition-colors focus:border-accent-500 focus:ring-accent-500"
							>
								<option value="">Select a service</option>
								<option value="strategy">Technical Strategy</option>
								<option value="architecture">Systems Architecture</option>
								<option value="hardware">Hardware Engineering</option>
								<option value="embedded">Embedded Systems</option>
								<option value="product">Product Development</option>
								<option value="diligence">Technical Due Diligence</option>
								<option value="other">Other</option>
							</select>
						</div>
					</div>

					<div>
						<label for="message" class="block text-sm font-medium text-slate-700"
							>Message</label
						>
						<textarea
							id="message"
							name="message"
							rows="5"
							required
							class="mt-1.5 block w-full rounded-lg border-slate-300 text-sm shadow-sm transition-colors focus:border-accent-500 focus:ring-accent-500"
							placeholder="Tell us about your project and what you're looking to achieve..."
						></textarea>
					</div>

					{#if status === 'error'}
						<p class="text-sm text-red-600">{errorMessage}</p>
					{/if}

					<button
						type="submit"
						disabled={status === 'submitting'}
						class="w-full rounded-lg bg-navy-900 px-6 py-3 text-sm font-semibold text-white shadow-sm transition-all hover:bg-navy-800 hover:shadow-md focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-accent-500 disabled:cursor-not-allowed disabled:opacity-60 sm:w-auto"
					>
						{status === 'submitting' ? 'Sending...' : 'Send Message'}
					</button>
				</form>
			{/if}
		</div>
	</div>
</section>
