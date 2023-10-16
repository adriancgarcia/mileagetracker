<script>
    export let trips;
    export let select;
    export let destroy;
    // export let calculate;

    
</script>


<div >
    <ul class="show">
        {#each trips as trip}
        <li on:click={() => select (trip)}>
            <h3>Trip Name: {trip.tripname}</h3>
            <h3>Date of Trip: {trip.tripdate}</h3>
            <h3>Beginning Mileage: {trip.startmileage}</h3>
            <h3>Ending Milage: {trip.endmileage}</h3>
            <h3>Cost Per Mile: {trip.costpermile}</h3>
            <h3>Mileage Reimbursement: {trip.reimbursement}</h3>
            <button on:click={() => destroy(trip)}>Delete</button>
        </li>
        {/each}
    </ul>
</div>

<style>
    .show {
        list-style-type: none;
        background-color: blueviolet;
        border: 3px solid hotpink;
    }
    .show:hover{
        cursor:pointer;
    }
</style>