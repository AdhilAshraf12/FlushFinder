<script>
	// When the user submits the reset form
	const resetPassword = (e) => {
		e.preventDefault();

		// In a real app, you would send a reset email here

		// Redirect back to sign in with a success message
		location.href = "/?resetSuccess=true";
	};
</script>

<div class="page-container">
	<div class="header-toggle">
		<div>
			<a href="/" class="selected">Sign in</a> 
			<a href="/signup">Register</a>
		</div>
	</div>

	<div class="logo-container">
		<img src="/FlushFinder.png" alt="FlushFinder Logo" />
	</div>

	<div class="form-container">
		<h2>Reset Password</h2>
		<p class="subtitle">Please enter the email associated with your FlushFinder Account</p>

		<form on:submit={resetPassword}>
			<label for="email">Email</label>
			<input type="email" id="email" placeholder="Your Email" required />

			<div class="button-group">
				<a href="/" class="cancel-btn">Cancel</a> 
				<button type="submit" class="submit-btn">Reset Password</button>
			</div>
		</form>
	</div>
</div>

<style>
	.page-container {
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		background: #f9fafb;
	}

	.header-toggle {
		display: flex;
		justify-content: flex-end;
		padding: 2rem;
	}

	.header-toggle > div {
		display: flex;
		column-gap: 0.5rem;
		background: #3f3d3d;
		border-radius: 100px;
		padding: 0.25rem;
	}

	.header-toggle a {
		text-decoration: none;
		padding: 0.5rem 1.5rem;
		border-radius: 100px;
		color: white;
		transition: all 0.2s ease;
	}

	.header-toggle a:hover:not(.selected) {
		background: rgba(255, 255, 255, 0.1);
	}

	.header-toggle .selected {
		background: #797fd2;
	}

	.logo-container {
		margin: 0svh auto;
	}

	.logo-container img {
		color: #7b7d94;
		text-decoration: none;
		margin: 0svh auto;
	}

	.form-container {
		max-width: 500px;
		width: 90%;
		margin: 0 auto;
		background: white;
		border-radius: 1rem;
		border: 1px solid #d9d9d9;
		padding: 2.5rem;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
	}

	h2 {
		margin: 0 0 0.5rem 0;
		color: #2c2c2c;
		font-size: 1.5rem;
	}

	.subtitle {
		color: #666;
		font-size: 0.9rem;
		margin: 0 0 2rem 0;
		line-height: 1.5;
	}

	form {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	label {
		font-weight: 500;
		color: #2c2c2c;
		margin-bottom: -0.5rem;
	}

	input {
		padding: 0.75rem 1rem;
		border: 1px solid #d9d9d9;
		border-radius: 0.5rem;
		font-size: 1rem;
		transition: border-color 0.2s ease;
	}

	input:focus {
		outline: none;
		border-color: #797fd2;
	}

	.button-group {
		display: flex;
		gap: 1rem;
		margin-top: 0.5rem;
	}

	.cancel-btn {
		flex: 1;
		padding: 0.75rem;
		text-align: center;
		text-decoration: none;
		color: #666;
		background: white;
		border: 1px solid #d9d9d9;
		border-radius: 0.5rem;
		font-weight: 500;
		transition: all 0.2s ease;
		cursor: pointer;
	}

	.cancel-btn:hover {
		background: #f5f5f5;
		border-color: #b0b0b0;
	}

	.submit-btn {
		flex: 2;
		padding: 0.75rem;
		background: #2c2c2c;
		color: white;
		border: none;
		border-radius: 0.5rem;
		font-weight: 400;
		font-size: 1rem;
		cursor: pointer;
		transition: all 0.2s ease;
	}

	.submit-btn:hover {
		background: #3f3f3f;
		transform: translateY(-1px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
	}

	.submit-btn:active {
		transform: translateY(0);
	}
</style>


<!-- <div><div><a href="/">Sign in</a> <a href="/signup">Register</a></div></div>
<div><img src="/FlushFinder.png" alt="rgw" /></div>

<form onsubmit={(e) => e.preventDefault()}>
	<h2>Please enter the email associated with your FlushFinder Account</h2>
	<label for="email">Email</label>
	<input type="email" placeholder="Your Email" required />
	<div><a href="/">Cancel</a> <button type="submit">Reset Password</button></div>
</form>

<style>
	img {
		margin: 0svh auto;
	}
	div > a {
		padding-top: 10svh;
		color: #7b7d94;
		text-decoration: none;
		margin: 0svh auto;
	}
	button {
		background-color: #2c2c2c;
		border: none;
		border-radius: 1rem;
		color: #f5f5f5;
		padding: 2svb;
		margin: 2svh 0svw;
	}
	form {
		border-radius: 1rem;
		border: 1px solid #d9d9d9;
		padding: 4svh 4svw;
		margin: 0svh 4svw;

		display: flex;
		flex-direction: column;
		row-gap: 2svh;
	}

	input {
		border-radius: 0.5rem;
		border: 1px solid #d9d9d9;
		padding: 1svh 1.5svw;
	}

	form a {
		color: #2c2c2c;
		margin: 0px;
		text-decoration: underline;
	}

	div {
		display: flex;
		justify-content: right;
	}

	form div {
		justify-content: space-evenly;
		align-items: center;
		text-align: center;
	}

	form > div > a {
		padding: 0px;
	}

	div > div {
		text-decoration: none;
		column-gap: 1svw;
		background: #3f3d3d;
		border-radius: 100px;
		margin: 4svh 2svw;
	}
	div > div > a {
		text-decoration: none;
		padding: 1svb 1.5svw;
		border-radius: 1rem;
		color: white;
	}
</style> -->