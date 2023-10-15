<script>
    export let trips;
    export let select;

    
</script>


<div >
    <ul class="show">
        {#each trips as trip}
        <li >
            <h3 on:click={() => select (trip)}>{trip.tripname}</h3>
            <h3>{trip.tripdate}</h3>
            <h3>{trip.startmileage}</h3>
            <h3>{trip.endmileage}</h3>
            <h3>{trip.costpermile}</h3>
        </li>
        {/each}
    </ul>
</div>

<style>
    .show {
        list-style-type: none;
    }
</style>