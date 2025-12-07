<script>
	import { userInfo } from '$lib/userInfoStore.js';

	// Detect success message from reset password redirect
	let resetSuccess = false;

	if (typeof window !== "undefined") {
		const params = new URLSearchParams(window.location.search);
		resetSuccess = params.get("resetSuccess") === "true";
	}

	const signIn = (e) => {
		e.preventDefault();

		let formData = new FormData(e.target);
		let formObject = Object.fromEntries(formData.entries());

		userInfo.setEmail(formObject.email);

		location.href = '/inapp/find';
	};
</script>

<div class="header-toggle">
	<div>
		<a href="/" class="selected">Sign in</a>
		<a href="/signup">Register</a>
	</div>
</div>

{#if resetSuccess}
	<div class="reset-success">
		✔ Email has been sent! Check your inbox.
	</div>
{/if}

<div><img src="/FlushFinder.png" alt="rgw" /></div>

<form onsubmit={(e) => signIn(e)}>
	<label for="email">Email</label>
	<input type="email" name="email" placeholder="first.last@gmail.com" required />

	<label for="password">Password</label>
	<input type="password" name="password" placeholder="Your password here" required />

	<button type="submit">Sign in</button>

	<a href="/forgotpassword">Forgot Password?</a>
</form>

<!-- Centered guest button -->
<div class="guest-container">
	<a
		class="guest-link"
		href="/inapp/find"
		onclick={() => {
			userInfo.setEmail('test@mail.com');
			userInfo.setGuestProfilePicture();
		}}
	>
		Continue as Guest
	</a>
</div>

<style>
	img {
		margin: 0 auto;
		display: block;
	}

	/* Success banner */
	.reset-success {
		background: #d1ffd6;
		color: #1b7a2f;
		padding: 1rem;
		text-align: center;
		border-radius: 0.5rem;
		margin: 1rem;
		font-weight: 600;
		border: 1px solid #8adf9a;
	}

	/* Guest button centered */
	.guest-container {
		display: flex;
		justify-content: center;
		margin-top: 5svh;
	}

	.guest-link {
		color: #7b7d94;
		text-decoration: none;
	}

	button {
		background-color: #2c2c2c;
		border: none;
		border-radius: 1rem;
		color: #f5f5f5;
		padding: 2svb;
		margin: 2svh 0;
	}

	button:hover {
		background: #3f3f3f;
		transform: translateY(-1px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
	}

	button:active {
		transform: translateY(0);
	}

	form {
		border-radius: 1rem;
		border: 1px solid #d9d9d9;
		padding: 4svh 4svw;
		margin: 0 4svw;

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
		margin: 0;
		text-decoration: underline;
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
</style>
