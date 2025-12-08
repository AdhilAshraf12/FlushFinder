<script>
	import { goto } from '$app/navigation';
    import devilledirections from '$lib/assets/devilledirections.png';
    import devillemap from '$lib/assets/devillemap.png';
</script>
<div class="pagecontent">
    <div>
        <img src={devillemap} class="devillemap"/>
        <button class="back" onclick={() => goto('/inapp/find')}> &lt; </button>
    </div>
    <!-- <div class="godirwrapper"> -->
        <img src={devilledirections} class="devilledirections"/>
        <button class="go" onclick={() => goto('/inapp/devillestart')}>
            GO
        </button>
    <!-- </div> -->
</div>

<style>
    .go {
	background: linear-gradient(135deg, #4f378b, #654cb5);
	color: white;
	border: none;
	border-radius: 10px;
	padding: 10px 14px;
	font-weight: 700;
	cursor: pointer;
	box-shadow: 0 8px 16px rgba(79, 55, 139, 0.28);
	transition: transform 0.1s ease, box-shadow 0.15s ease;
}
   .back{
        position: absolute;
        top: 10px;
        left: 5px;
        border-radius: 100%;
        border: none;
        color: black;
        font-size: 35px;
        background-color: transparent;
    }

.pagecontent {
    min-height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;   
    overflow: hidden;
}

.devillemap {
    height: 70vh;
    width: auto;     
    max-width: 900px; 
    object-fit: contain;
}
.devilledirections {
    width: 100%;      
    max-width: 278px;  
    height: auto;
    object-fit: contain;
}

.FSbutton {
    background-color: #4F378B;
    padding: 12px 24px; 
    color: white;
    border-radius: 100px;
    border: none;
    font-size: 16px;
    white-space: nowrap;
    flex-shrink: 0; 
}

@media (max-width: 768px) {
    .godirwrapper {
        flex-direction: column;
        gap: 12px;
        max-width: 100%;
        padding: 12px;
    }

    .devilledirections {
        width: 100%;
        max-width: 100%;
    }

    .FSbutton {
        width: auto;
    }
}


</style>