<script>
    export let tripname
    export let tripdate
    export let startmileage
    export let endmileage
    export let costpermile
    export let _id
    export let action 
    export let create 

    function calculate() {
      let startmileage = parseFloat(document.getElementById('startmileage').value);
      let endmileage = parseFloat(document.getElementById('endmileage').value);
      let costpermile = parseFloat(document.getElementById('costpermile').value);
      
      let distance = endmileage - startmileage;
      let mileage = distance * costpermile;
  
      document.getElementById('outputDiv').innerHTML = mileage;
      // console.log(mileage)
    }

    const handleSubmit = (event) => {
        event.preventDefault()
        if(action === "create"){
            create({tripname, tripdate, startmileage, endmileage, costpermile})
        }
        if(action === "update"){

        }
    }
    
</script>


<div>
<form on:submit={handleSubmit}>
    <label for="tripname">Trip Name</label>
    <input type=text bind:value={tripname}>
    <label for="tripdate">Date of Trip</label>
    <input type=date bind:value={tripdate}>
    <label for="startmileage">Trip Beginning</label>
    <input type=number bind:value={startmileage}>
    <label for="endmileage">Trip End</label>
    <input type=number bind:value={endmileage}>
    <label for="costPerMile">Cost Per Mile</label>
    <input type=float bind:value={costpermile}> 
    <div>
    <button type="button" on:click={calculate}>Calculate Amount</button>
    </div>
    <br>
    <div>
    Amount Reimbursed<div id="outputDiv"></div>
    </div>
    <input type=submit>
</form>
    
</div>