<script>
	import { userInfo } from '$lib/userInfoStore';
	import { goto } from '$app/navigation';
	import map from '$lib/assets/mapsimage.png';




	let showFilter = $state(false);
	let distance = $state(0);
	let rating = $state(0);
	let gender = $state(''); 

	$effect(() => {
		if (userInfo.getEmail() == '') {
			location.href = '/';
		}
	});


//------------------------------
    // Filter popup functions

	function toggleFilter() {
		showFilter = !showFilter;
		console.log('Toggled Filter Popup:', showFilter);
	}

	function closeFilter() {
		showFilter = false; 
		distance = 0;
		rating = 0;
		gender = "";

		console.log("Selected rating:", rating);
		console.log("Selected gender:", gender);
		console.log("Distance:", distance);
	}



	function handleDistanceChange(event) {
		distance = event.target.value;
	}

    function saveRating(value) {
		    if (rating === value && value === 1) {
        rating = 0;
    } else {
        rating = value;
    }
 
        console.log("Selected rating:", rating);
    }

	function handleGenderChange(event) {
		gender = event.target.value;
		console.log('Selected gender:' , gender);
	}

	function selectGender(value) {
	if (gender === value) {
		// Clicking the same button again unselects it
		gender = '';
	} else {
		gender = value;
	}
	console.log('Selected gender:', gender);
}



//-------------------------------


</script>

<form class="searchbar-full"
	onsubmit={(e) => {
		e.preventDefault();
		console.log('Hello');
	}}
>
	<div class="div-search">
		<button type="menu">
			<img src="https://www.svgrepo.com/show/524617/hamburger-menu.svg" alt="Hamburger" />
		</button>
		<input type="text" placeholder="Search for bathrooms" class="search-bar"/>
		<button type="submit" class="searchicon">
			<img src="https://www.svgrepo.com/show/532552/search-alt-2.svg" alt="Search Icon" />
		</button>
	</div>
</form>

<div class="filterbuttons">
	<span>
		<button class="FSbutton" onclick={toggleFilter}>Filter</button>
		<button class="FSbutton">See All</button>
	</span>
</div>


{#if showFilter}
	<div class="filter-popup-overlay">
		<div class="filter-popup">
			<form>
						<button class="close-btn" onclick={closeFilter}>✕</button>

<label for="distance">Distance</label>
<input 
  id="distance"
  type="range" 
  min="0" 
  max="10" 
  step="0.1"
  bind:value={distance}
  oninput={handleDistanceChange} 
/>
<div class ='DistanceValue'>{distance} km</div>

				<br />
<label>
    Minimum Rating
    <br />
    <div style="display: flex; gap: 5px; cursor: pointer;">
        {#each [1,2,3,4,5] as star}
            <button class="star-button" 
                onclick={() => saveRating(star)}
                style="
    font-size: 30px;
    color: {star <= rating ? 'gold' : 'transparent'};
    -webkit-text-stroke: 1px gold;
"
            >
                ★
	</button>
        {/each}
    </div>
</label>

				<br />
				<label>
    Gender
    <div style="display: flex; gap: 10px; margin-top: 8px;">
        <!-- Male button -->
        <button id ='male-button'
            type="button"
            onclick={() => selectGender('male')}
            class:selected={gender === 'male'}
        >
		    <span class="gender-symbol">♂</span>
    		<span class="gender-text">Male</span>
	
        </button>

        <!-- Female button -->
        <button id ='female-button'
            type="button"
            onclick={() => selectGender('female')}
            class:selected={gender === 'female'}
        >

			<span class="gender-symbol"> ♀ </span>
    		<span class="gender-text">Female</span>
	
           
        </button>

        <!-- Neutral button with ⚥ symbol -->
        <button id ='neutral-button'
            type="button"
            onclick={() => selectGender('neutral')}
            class:selected={gender === 'neutral'}
        >
			<span class="gender-symbol">⚥ </span>
    		<span class="gender-text">Neutral</span>
        </button>
    </div>
</label>
				<br />
				<label>
					Accessibility:
					<br />
					<input type="checkbox" /> Wheelchair
					<input type="checkbox" /> Changing Table
					<input type="checkbox" /> Paid Accessibility
				</label>
				<br />
				<button type="button" class="apply-button" onclick={toggleFilter}>Apply</button>
			</form>
		</div>
	</div>
{/if}

<div class="nearbylocations">
	<div class="buttonrow">
		<button class="locationbut">
			Deville Coffee Washroom
			<small class="small">100 m&nbsp;&nbsp;&nbsp;&nbsp;2 min  🚻    ♿</small>
		</button>
		<div class="gocol">
			<div>⭐️⭐️⭐️⭐️⭐️</div>
			<button class="FSbutton" onclick={() => goto('/inapp/deville')}>GO</button>
		</div>
	</div>		
	<div class="buttonrow">
		<button class="locationbut">
			BVC Main floor Washroom
			<small class="small">300 m&nbsp;&nbsp;&nbsp;&nbsp;6 min&nbsp; ⚧    ♿</small>
		</button>
		<div class="gocol">
			<div>⭐️⭐️⭐️⭐️</div>
			<button class="FSbutton">GO</button>
		</div>
	</div>	
	<div class="buttonrow">
		<button class="locationbut">
			Superstore Washroom
			<small class="small">350 m&nbsp;&nbsp;&nbsp;&nbsp;8 min  🚻    ♿</small>
		</button>
		<div class="gocol">
			<div>⭐️⭐️⭐️</div>
			<button class="FSbutton">GO</button>
		</div>
	</div>	
</div>


<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
	.gocol{
		display:flex;
		flex-direction: column;
		align-items: center;
		width: 90px;
	}

	.small{
		color: #757575;
	}

	.buttonrow{
		display:flex;
		flex-direction: row;
		padding-right: 5px;
	}
	.locationbut{
		background-color: white;
		margin: 10px;
		color: 1E1E1E;
		font-size: 18px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding: 0 10px;
		height: auto;
		width: 235px;
		text-align: left;
		align-items: flex-start;
	}

	.nearbylocations{
		border: 1px solid #D9D9D9;
		box-shadow: 0px 4px 4px 0px rgb(0, 0, 0, 0.25);
		border-radius: 8px;
		height: 220px;
		width: 360px;
		display: flex;
		flex-direction: column;
		margin-left: auto;
  		margin-right: auto;
		justify-content: space-evenly;
	}

	.searchicon{
		margin-left: auto;
		border-radius: 15px;
	}

	img {
		width: 30px;
		aspect-ratio: 1;
	}
	
	.FSbutton{
		background-color: #4F378B;
		height: 29px;
		width: 68px;
		color: white;
		border-radius: 100px;
		cursor: pointer;
	}

	.filterbuttons span{
		display:flex;
		justify-content: space-between;
		padding-top: 1%;
		padding-bottom: 1%;
	}

	.div-search {
		display: flex;
		background-color: #ECE6F0;
		align-items: center;
		justify-content: left;
		height: 56px;
		width: 360px;
		border-radius: 40px;
		padding-left: 10px;
	}

	.search-bar{
		background-color: #ECE6F0;
		height: 28px;
		width: 360px;
		border: none;
		outline: none;
	}

	button{
		background-color: #ECE6F0;
		border: none;
	}

	.searchbar-full{
		display: flex;
		justify-content: top;
		flex-direction: column;
		background-image: url('$lib/assets/mapsimage.png');
		height: 350px;
		width: 100%;
	}

	/* Filter Popup Styles */
	.filter-popup-overlay {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.5);
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 1000;
	}

	.filter-popup {
		background-color: white;
		padding: 20px;
		border-radius: 12px;
		width: 300px;
		box-shadow: 0 5px 15px rgba(0,0,0,0.3);
	}

	 label {
  display: block;       /* label on its own line */
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  margin-bottom: 10px; /* space below label */
}

.DistanceValue{
	font-family: 'Inter', sans-serif;
	font-size: 14px;}

    
		#distance {
			width: 100%;
			height: 20px;
			border-radius: 8px;
			background: #E8DEF8;
			accent-color: #6750A4; ;
			outline: none;
			margin-top: 8px;
			margin-bottom: 8px;
		
		}

		.star-button {
			background: none;
			border: none;
			cursor: pointer;
			padding: 0;
			margin: 0;
		}


		 /* Common button styles */
    #male-button,
    #female-button,
    #neutral-button {
        padding: 8px 16px;
        border-radius: 8px;
        border: 1px solid #ccc;
        background-color: white;
        cursor: pointer;
        font-size: 14px;
        transition: all 0.2s;
    }

    /* Selected styles */
    #male-button.selected,
    #female-button.selected,
    #neutral-button.selected {
        background-color: #E8DEF8;
        border-color: #6750A4;
    }

	.gender-text {
		font-family: 'Inter', sans-serif;
		font-size: 14px;
		font-weight: 500;
		color: #4F378B;
	}

	.close-btn {
	
	font-size: 18px;
	color: #757575;
	cursor: pointer;
	background-color: white;
	border: none;
	margin-left: 90%;
}


.apply-button {
	background-color: #4F378B;
		height: 29px;
		width: 68px;
		color: white;
		border-radius: 100px;
		cursor: pointer;
		margin-top: 10px;
		margin-left: 40%;	
}




	
</style>
