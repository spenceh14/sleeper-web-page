<!-- LoginForm.svelte -->

<script>
  import { onMount } from 'svelte';

  let username = '';
  let password = '';
  let error = '';

  const handleSubmit = async () => {
    try {
      // Fetch user data from user.json (assuming it's in the same directory as the script)
      const response = await fetch('/users.json');
      const users = await response.json();

      // Check if the entered username and password are correct
      const isValidUser = users.find(user => user.username === username && user.password === password);

      if (isValidUser) {
        // Redirect to '/home' if the user is valid
        window.location.href = '/home';
      } else {
        // Display an error message if the credentials are incorrect
        error = 'Invalid username or password';
      }
    } catch (error) {
      console.error('Error fetching user data', error);
    }
  };
</script>

<style>
  /* Add your styles here */
</style>

<form on:submit|preventDefault={handleSubmit}>
  <label for="username">Username:</label>
  <input type="text" id="username" bind:value={username} />

  <label for="password">Password:</label>
  <input type="password" id="password" bind:value={password} />

  {#if error}
    <p style="color: red;">{error}</p>
  {/if}

  <button type="submit">Login</button>
</form>
