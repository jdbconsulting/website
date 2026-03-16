<script lang="ts">
	interface Props {
		heading?: string;
		body?: string;
		buttonText?: string;
		buttonHref?: string;
		backgroundImage?: string;
	}

	let {
		heading = 'Ready to Build Something Exceptional?',
		body = "Let's discuss how excellent electrical engineering leadership can accelerate your next project.",
		buttonText = 'Start a Conversation',
		buttonHref = '/contact',
		backgroundImage = ''
	}: Props = $props();
</script>

<section class="relative overflow-hidden bg-navy-950 py-20 sm:py-28">
	{#if backgroundImage}
		<img
			src={backgroundImage}
			alt=""
			class="absolute inset-0 h-full w-full object-cover brightness-[0.3]"
			aria-hidden="true"
		/>
	{/if}
	<div
		class="absolute inset-0 bg-[radial-gradient(ellipse_at_bottom_left,rgba(245,158,11,0.08),transparent_60%)]"
		aria-hidden="true"
	></div>
	<div class="relative mx-auto max-w-7xl px-4 text-center sm:px-6 lg:px-8">
		<h2 class="mx-auto max-w-2xl text-3xl font-bold tracking-tight text-white sm:text-4xl">
			{heading}
		</h2>
		<p class="mx-auto mt-4 max-w-xl text-lg leading-relaxed text-slate-300">{body}</p>
		<a
			href={buttonHref}
			class="mt-8 inline-block rounded-lg bg-accent-500 px-8 py-3.5 text-sm font-semibold text-navy-950 shadow-sm transition-all hover:bg-accent-400 hover:shadow-md focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-accent-500"
		>
			{buttonText}
		</a>
	</div>
</section>
