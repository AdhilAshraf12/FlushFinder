<!-- <script>
	import { page } from '$app/stores';
	import { userInfo } from '$lib/userInfoStore';
	import Icon from '$lib/assets/Icon.png';

	let { children } = $props();
</script>
  
{@render children?.()}
<nav>
	<a href="/inapp/find" class:selected={$page.url.pathname === '/inapp/find'}
		><img src="https://www.svgrepo.com/show/529715/map-point-wave.svg" alt="Pin Icon" /><span
			>Find</span
		></a
	>

	<a href="/inapp/review" class:selected={$page.url.pathname === '/inapp/review'}
		><img src={Icon} alt="Review Icon" class="revicon"/><span>Review</span></a
	>
	<a href="/inapp/profile" class:selected={$page.url.pathname === '/inapp/profile'}
		><img src={userInfo.getProfilePicture()} alt="Profile Icon" /><span>Profile</span></a
	>
</nav>

<style>
	span {
		display: block;
	}
	img {
		width: 50px;
		aspect-ratio: 1;
		padding: 6px;
		border-radius: 50%;
		object-fit: contain;
	}

	.revicon{
		
	}

	a {
		display: flex;
		flex-direction: column;
		text-align: center;
		text-decoration: none;
		cursor: pointer;
		justify-content: center;
		border-radius: 1rem;
	}

	nav {
		display: flex;
		background-color: #BBBFEF;
		border-top-left-radius: 4svb;
		border-top-right-radius: 4svb;
		padding: 1svb;
		justify-content: center;
		justify-content: space-evenly;
		bottom: 0;
	}

	.selected {
		background-color: white;
	}

</style>
 -->




<!-- src/routes/inapp/+layout.svelte -->
<script>
	import { page } from '$app/stores';

	let { children } = $props();
</script>

<!-- Main content area -->
<div class="pb-20">
	{@render children?.()}
</div>

<!-- Fixed bottom navigation -->
<nav class="fixed bottom-0 left-0 right-0 bg-purple-100 shadow-lg z-50">
	<div class="flex items-center justify-around px-6 py-4 max-w-md mx-auto">
		<a 
			href="/inapp/find" 
			class="flex flex-col items-center gap-1 transition-colors {$page.url.pathname === '/inapp/find' ? 'text-purple-700' : 'text-gray-600'}"
		>
			<svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
				<path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
				<circle cx="12" cy="10" r="3"></circle>
			</svg>
			<span class="text-xs">Find</span>
		</a>

		<a 
			href="/inapp/review" 
			class="flex flex-col items-center gap-1 transition-colors {$page.url.pathname === '/inapp/review' ? 'text-purple-700' : 'text-gray-600'}"
		>
			<svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
				<path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
				<polyline points="14 2 14 8 20 8"></polyline>
				<line x1="16" y1="13" x2="8" y2="13"></line>
				<line x1="16" y1="17" x2="8" y2="17"></line>
				<polyline points="10 9 9 9 8 9"></polyline>
			</svg>
			<span class="text-xs">Review</span>
		</a>

		<a 
			href="/inapp/profile" 
			class="flex flex-col items-center gap-1 px-8 py-2 rounded-full transition-all {$page.url.pathname === '/inapp/profile' ? 'bg-white text-purple-700 shadow' : 'text-gray-600'}"
		>
			<svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
				<path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
				<circle cx="12" cy="7" r="4"></circle>
			</svg>
			<span class="text-xs">Profile</span>
		</a>
	</div>
</nav>

<style>
	* {
		font-family: 'Ubuntu', sans-serif;
	}
</style>