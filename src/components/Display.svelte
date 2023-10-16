<script>
    export let trips;
    export let select;
    export let destroy;

    
</script>


<div >
    <ul class="show">
        {#each trips as trip}
        <li on:click={() => select (trip)}>
            <h3>{trip.tripname}</h3>
            <h3>{trip.tripdate}</h3>
            <h3>{trip.startmileage}</h3>
            <h3>{trip.endmileage}</h3>
            <h3>{trip.costpermile}</h3>
            <button on:click={() => destroy(trip)}>Delete</button>
        </li>
        {/each}
    </ul>
</div>

<style>
    .show {
        list-style-type: none;
    }
    .show:hover{
        cursor:pointer;
    }
</style>