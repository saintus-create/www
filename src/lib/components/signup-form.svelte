<script lang="ts">
	import { Button } from '$lib/components/ui/button'
	import { Input } from '$lib/components/ui/input'
	import { Label } from '$lib/components/ui/label'

	let email = ''
	let company = ''
	let submitting = false
	let success = false

	async function handleSubmit(event: SubmitEvent) {
		event.preventDefault()
		if (submitting) return
		submitting = true
		await new Promise((resolve) => setTimeout(resolve, 1000))
		success = true
		email = ''
		company = ''
		submitting = false
	}
</script>

<form on:submit={handleSubmit} class="space-y-6">
	<header class="space-y-2">
		<p class="text-xs font-medium text-muted-foreground">Early access</p>
		<h2 class="text-xl font-semibold tracking-tight text-foreground">Request a walkthrough</h2>
		<p class="text-sm text-muted-foreground">We respond within one business day.</p>
	</header>

	<div class="space-y-2">
		<Label for="email">Email</Label>
		<Input
			id="email"
			type="email"
			placeholder="you@studio.com"
			bind:value={email}
			required
		/>
	</div>

	<div class="space-y-2">
		<Label for="company">Company</Label>
		<Input id="company" type="text" placeholder="Studio name" bind:value={company} />
	</div>

	<Button type="submit" class="w-full" disabled={submitting}>
		{submitting ? 'Sending…' : success ? 'Request sent' : 'Send request'}
	</Button>
</form>
