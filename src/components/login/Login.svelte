<script>
  let email = '';
  let password = '';
  let error = '';
  let isLoading = false;
console.log("");
  async function handleLogin() {
    isLoading = true;
    error = '';

    if (!email || !password) {
      error = 'Please fill in all fields';
      isLoading = false;
      return;
    }

    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      
      // Mock authentication using dummy data
      if (email === 'user@example.com' && password === 'password123') {
        alert('Login successful!');
        email = '';
        password = '';
      } else {
        error = 'Invalid email or password';
      }
    } catch (err) {
      error = 'An error occurred. Please try again.';
    } finally {
      isLoading = false;
    }
  }

  function handleKeydown(e) {
    if (e.key === 'Enter') {
      handleLogin();
    }
  }
</script>

<div class="login-container">
  <div class="login-box">
    <h1>Login</h1>
    
    {#if error}
      <div class="error-message">{error}</div>
    {/if}

    <form on:submit|preventDefault={handleLogin}>
      <div class="form-group">
        <label for="email">Email</label>
        <input
          id="email"
          type="email"
          bind:value={email}
          placeholder="user@example.com"
          on:keydown={handleKeydown}
          disabled={isLoading}
        />
      </div>

      <div class="form-group">
        <label for="password">Password</label>
        <input
          id="password"
          type="password"
          bind:value={password}
          placeholder="Enter your password"
          on:keydown={handleKeydown}
          disabled={isLoading}
        />
      </div>

      <button type="submit" disabled={isLoading}>
        {isLoading ? 'Logging in...' : 'Login'}
      </button>
    </form>

    <p class="hint">Demo credentials: user@example.com / password123</p>
  </div>
</div>

<style>
  .login-container {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
  }

  .login-box {
    background: white;
    border-radius: 8px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
    padding: 40px;
    width: 100%;
    max-width: 400px;
  }

  h1 {
    text-align: center;
    color: #333;
    margin: 0 0 30px 0;
    font-size: 28px;
  }

  .error-message {
    background-color: #fee;
    color: #c33;
    padding: 12px;
    border-radius: 4px;
    margin-bottom: 20px;
    font-size: 14px;
    border-left: 4px solid #c33;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  label {
    font-weight: 500;
    color: #555;
    font-size: 14px;
  }

  input {
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
    transition: border-color 0.3s ease;
  }

  input:focus {
    outline: none;
    border-color: #667eea;
    box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
  }

  input:disabled {
    background-color: #f5f5f5;
    cursor: not-allowed;
  }

  button {
    padding: 12px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    margin-top: 10px;
  }

  button:hover:not(:disabled) {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
  }

  button:active:not(:disabled) {
    transform: translateY(0);
  }

  button:disabled {
    opacity: 0.7;
    cursor: not-allowed;
  }

  .hint {
    text-align: center;
    color: #999;
    font-size: 12px;
    margin-top: 20px;
    margin-bottom: 0;
  }
</style>
