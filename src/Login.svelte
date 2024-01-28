svelte
<script>
  let username = "";
  let password = "";

  async function handleLogin() {
    const response = await fetch("/api/login", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify({ username, password })
    });

    if (response.ok) {
      // Redirect user to dashboard or authorized route
    } else {
      // Handle login error
    }
  }
</script>

<form on:submit|preventDefault={handleLogin}>
  <label for="username">Username:</label>
  <input type="text" id="username" bind:value={username} />

  <label for="password">Password:</label>
  <input type="password" id="password" bind:value={password} />

  <button type="submit">Login</button>
</form>