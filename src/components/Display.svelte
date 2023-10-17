<script>
    export let trips;
    export let select;
    export let destroy;
    // export let calculate;

    
</script>


<div>
    <ul class="show">
        {#each trips as trip}
            <li>
                <h3>Trip Name: {trip.tripname}</h3>
                <h3>Date of Trip: {trip.tripdate}</h3>
                <h3>Beginning Mileage: {trip.startmileage}</h3>
                <h3>Ending Milage: {trip.endmileage}</h3>
                <h3>Cost Per Mile: {trip.costpermile}</h3>
                <h3>Mileage Reimbursement: ${trip.reimbursement}</h3>
                <button class="editButton" on:click ={() => select (trip)}>Edit Trip</button>
                <button class ="deleteButton" on:click={() => destroy(trip)}>Delete</button>
            </li>
        {/each}
    </ul>
</div>

<style>
    .show {
        padding-bottom: 60px;
    }
    ul{
        margin: 0 auto;
        padding: 0;
    }
    .show li {
        list-style-type: none;
        padding: 20px;
        
    }
    li {
        background: black;
        opacity: .7;
        border: 3px solid white;
        width: 350px;
        padding: 0;
        margin: 0;
        display: grid;
        gap: 1em;
        grid-template-columns: repeat(auto-fill, minmax(200px, 100%), 1fr);
    }
    h3{ 
        color: white;
        margin: 0;
        padding: 0 30px;
    }
    .show:hover{
        cursor:pointer;
    }
    .editButton {
        width: 50%;
        align-items: center;
        text-align: center;
        margin: 0 auto;
    }
    .deleteButton {
        width: 50%;
        /* margin: 20px; */
        align-items: center;
        text-align: center;
        margin: 0 auto;
    }


</style>