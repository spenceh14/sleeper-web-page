<script>
	import { user } from '$lib/store'
	import { onDestroy } from 'svelte'
	let user_value
	user.subscribe((u) => (user_value = u))
	let unsubscribe = user.subscribe((u) => (user_value = u))
	let email
	let password
	function handleLogin() {
		if (!email || !password) {
			alert('please enter your credentials')
			return
		}

		// By the way, you MUST return the values to the store, otherwise
		// it will end up as undefined, which is bad
		user.update((u) => u = JSON.stringify({ email: email, password: password }))
	}
	function handleLogout() {
		user.update((u) => (u = ''))
	}
	$: console.log(user_value)
	onDestroy(unsubscribe)
</script>
<svelte:head>
	<title>Local Storage Stores Login</title>
</svelte:head>
{#if !user_value}
	<input type="email" bind:value={email} placeholder="enter email" />
	<input type="password" bind:value={password} placeholder="enter password" />
	<button on:click={handleLogin}>Login</button>
{:else if user_value}
	<h3>You are logged in as: {JSON.parse(user_value).email}</h3>
	<button on:click={handleLogout}>Logout</button>
{/if}