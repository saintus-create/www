<script lang="ts">
	const logos = [
		{ name: 'Calvin Klein', src: '/logos/calvin-klein.svg' },
		{ name: 'Lockheed Martin', src: '/logos/lockheed-martin.svg' },
		{ name: 'Guess Triangle', src: '/logos/guess-triangle.svg' },
		{ name: 'Guess Wordmark', src: '/logos/guess-word.svg' },
		{ name: 'Royal Rangers', src: '/logos/royal-rangers.svg' },
		{ name: 'Her Justice', src: '/logos/her-justice.svg' },
		{ name: 'National Domestic Violence Hotline', src: '/logos/national-domestic-violence-hotline.svg' },
		{ name: 'First Filipino Regiment', src: '/logos/first-filipino-regiment.svg' },
	];

	const marqueeItems = [...logos, ...logos];
</script>


<div class="relative overflow-hidden rounded-lg border bg-muted/30 px-4 py-4 [mask-image:linear-gradient(90deg,transparent,black_15%,black_85%,transparent)]">
	<div class="flex gap-6 animate-stack-marquee">
			{#each marqueeItems as stack}
				<div class="min-w-[9rem] max-w-[11rem] rounded-md border border-border bg-card px-4 py-3 flex items-center justify-center">
					<img src={stack.src} alt={stack.name} class="w-full h-auto object-contain opacity-90" />
					<span class="sr-only">{stack.name}</span>
				</div>
			{/each}
		</div>
	</div>
