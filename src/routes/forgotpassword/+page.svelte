<p>Please enter the email associated with your FlushFinder Account</p>
<form onsubmit={(e) => e.preventDefault()}>
	<label for="email">Email</label>
	<input type="email" placeholder="Your Email" required />
	<div><a href="/">Cancel</a> <button type="submit">Reset Password</button></div>
</form>

<style>
	a {
		text-decoration: none;
		color: inherit;
	}

	form {
		border: 1px solid lightgrey;
		border-radius: 1rem;
		width: 50svw;
		padding: 4svb;
		margin: 0svh auto;
		display: flex;
		flex-direction: column;
		row-gap: 2svh;
	}

	div {
		display: flex;
		justify-content: space-evenly;
		align-items: center;
	}

	button {
		background-color: #2c2c2c;
		color: #a4a4a4;
		border: none;
		border-radius: 1rem;
		padding: 2svb;
	}
</style>
