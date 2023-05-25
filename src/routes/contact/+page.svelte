<script>
	let name = '';
	let email = '';
	let message = '';

	async function handleSubmit() {
		const res = await fetch('/api/sendmail', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify({ name, email, message })
		});
		if (res.ok) {
			alert('Thank you for your message. We will get back to you soon!');
			name = '';
			email = '';
			message = '';
		} else {
			alert('Something went wrong. Please try again.');
		}
	}
</script>

<div class="flex flex-row">
	<form on:submit|preventDefault={handleSubmit} class="flex flex-col">
		<label>
			Name
			<input type="text" bind:value={name} required />
		</label>
		<label>
			Email
			<input type="email" bind:value={email} required />
		</label>
		<label>
			Message
			<textarea bind:value={message} required />
		</label>
		<button type="submit">Submit</button>
	</form>
</div>
