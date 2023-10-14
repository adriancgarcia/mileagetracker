<script>
    export let trips;

    
</script>


<div>
    <ul>
        {#each trips as trip}
            <li>
                <h3>{trip.completed}</h3>
            </li>
        {/each}
        
    </ul>


</div>