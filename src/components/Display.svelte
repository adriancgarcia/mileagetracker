<script>
    export let trips;
    export let select;
    export let destroy;
</script>


<div class="tripList">
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
    .tripList ul{
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        align-content: space-around;
        /* margin: 0 10px 0 10px; */
    }

    .show {
        padding:0;
    }

    .show ul{
        margin: 0 auto;
        /* padding-bottom: 20px; */
    }

    .show li {
        list-style-type: none;
        padding: 20px;  
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        align-content: center;
    }

    li {
        background-color: rgba(0, 0, 0, .8);
        border: 3px solid white;
        width: 300px;
        padding: 0;
        padding-bottom: 20px;
        margin: 20px;
        /* display: grid;
        gap: 1em;
        grid-template-columns: repeat(auto-fill, minmax(200px, 100%), 1fr); */
    }

    h3 { 
        color: white;
        margin: 0;
        padding: 0 30px;
    }

    .editButton {
        width: 40%;
        align-items: center;
        text-align: center;
        margin: 0 auto;
        margin-top: 20px;
    }

    .deleteButton {
        width: 40%;
        /* margin: 20px; */
        align-items: center;
        text-align: center;
        margin: 0 auto;
        margin-top: 20px;
    }

    button {
        display:inline-block;
        padding:0.7em 1.4em;
        margin:0 0.3em 0.3em 0;
        border-radius:6px;
        box-sizing: border-box;
        text-decoration:none;
        font-family:'Roboto',sans-serif;
        text-transform:uppercase;
        font-weight:400;
        color:#FFFFFF;
        background-color:#3369ff;
        box-shadow:inset 0 -0.6em 0 -0.35em hsla(0, 0%, 0%, 0.17);
        text-align:center;
        position:relative;
    }
    
    button:active {
        top: 0.1em;
    }
    
    @media all and (max-width:30em) {
        button{
            display:block;
            margin:0.4em auto;
        }
    }
    
    button:hover {
        cursor: pointer;
    }
</style>