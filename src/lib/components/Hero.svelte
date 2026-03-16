<script lang="ts">
	interface Props {
		title: string;
		subtitle: string;
		primaryCta?: string;
		primaryHref?: string;
		secondaryCta?: string;
		secondaryHref?: string;
		centered?: boolean;
		dark?: boolean;
		compact?: boolean;
		backgroundImage?: string;
	}

	let {
		title,
		subtitle,
		primaryCta = '',
		primaryHref = '/contact',
		secondaryCta = '',
		secondaryHref = '/case-studies',
		centered = true,
		dark = true,
		compact = false,
		backgroundImage = ''
	}: Props = $props();
</script>

<section class="relative overflow-hidden {dark ? 'bg-navy-950' : 'bg-white'}">
	{#if backgroundImage}
		<img
			src={backgroundImage}
			alt=""
			class="absolute inset-0 h-full w-full object-cover brightness-[0.3]"
			aria-hidden="true"
		/>
	{/if}
	{#if dark}
		<div
			class="absolute inset-0 bg-[radial-gradient(ellipse_at_top_right,rgba(59,130,246,0.12),transparent_60%)]"
			aria-hidden="true"
		></div>
	{/if}
	<div
		class="relative mx-auto max-w-7xl px-4 sm:px-6 lg:px-8
			{compact ? 'py-16 sm:py-20 lg:py-24' : 'py-24 sm:py-32 lg:py-40'}
			{centered ? 'text-center' : ''}"
	>
		<h1
			class="mx-auto max-w-4xl text-4xl font-bold tracking-tight sm:text-5xl lg:text-6xl
				{dark ? 'text-white' : 'text-slate-900'}"
		>
			{title}
		</h1>
		<p
			class="mx-auto mt-6 max-w-2xl text-lg leading-relaxed sm:text-xl
				{dark ? 'text-slate-300' : 'text-slate-600'}"
		>
			{subtitle}
		</p>
		{#if primaryCta || secondaryCta}
			<div class="mt-10 flex flex-wrap items-center gap-4 {centered ? 'justify-center' : ''}">
				{#if primaryCta}
					<a
						href={primaryHref}
						class="rounded-lg bg-accent-500 px-6 py-3 text-sm font-semibold text-navy-950 shadow-sm transition-all hover:bg-accent-400 hover:shadow-md focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-accent-500"
					>
						{primaryCta}
					</a>
				{/if}
				{#if secondaryCta}
					<a
						href={secondaryHref}
						class="rounded-lg px-6 py-3 text-sm font-semibold transition-colors
							{dark
							? 'text-white ring-1 ring-white/20 hover:bg-white/10'
							: 'text-slate-700 ring-1 ring-slate-300 hover:bg-slate-50'}"
					>
						{secondaryCta}
					</a>
				{/if}
			</div>
		{/if}
	</div>
</section>
