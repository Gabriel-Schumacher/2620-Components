<script>
    let active = false
    let formSubmitted = false
    
    let requiredInputs = [
    {
        input: 'Name',
        type: 'text',
        sample:'John Doe',
        value: '',
        valid: true
    },
    {
        input: 'Social Security Number, or ITIN',
        type: 'text',
        sample: 'SSN, or ITIN',
        value: '',
        valid: true
    },
    {
        input: 'Email',
        type: 'email',
        sample:'johnsmith@sample.com',
        value: '',
        valid: true
    }
]

function handleSubmit() {
    formSubmitted = true
    let allValid = true

    requiredInputs.forEach(input => {
        input.valid = input.value.trim() !== ''
        if(!input.valid) {
            allValid = false
        }
    })
    if (allValid && active) {
        alert('Your account has been created!')
    }
    console.log('Form has been submitted!')
}

</script>

<div class="m-4 mx-auto card p-4 w-1/2">
    <h1>Create your Account!</h1>
	<form on:submit|preventDefault={handleSubmit}>
        {#each requiredInputs as input}
        <label class="label my-4">
            <p>{input.input}</p>
            {#if input.type === 'text'}
            <input class="text-secondary-800 w-1/2" type='text' placeholder={input.sample} required bind:value={input.value}>
            {:else if input.type === 'email'}
            <input class="text-secondary-800 w-1/2" type='email' placeholder={input.sample} required bind:value={input.value}>
            {/if}
        </label>
        {/each}
		<label class="label">
			<input class="m-4 checkbox" type="checkbox" bind:checked={active} />
			Yes! I agree to terms and conditions!
		</label>
		{#if active}
			<p>Thank you. You can now create your account!</p>
		{:else}
			<p>You must agree to terms and conditions to create your account.</p>
		{/if}

		<button class="btn variant-filled-primary" type="submit" disabled={!active}>Sign Up</button>
	</form>
</div>