<script lang="ts">
	import {
		Card,
		CardContent,
		CardDescription,
		CardHeader,
		CardTitle,
	} from '$lib/components/ui/card';

	export let title = '';
	export let subtitle = '';
</script>

<Card class="col-span-12 md:col-span-6 border-border transition hover:-translate-y-0.5">
	<CardHeader class="pb-2">
		<CardTitle class="text-base font-medium">{title}</CardTitle>
		<CardDescription>Detail</CardDescription>
	</CardHeader>
	<CardContent>
		<p class="text-sm text-muted-foreground leading-relaxed">{subtitle}</p>
	</CardContent>
</Card>
