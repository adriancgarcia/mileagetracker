<script>

// function calculate() {
//       let startmileage = (document.getElementById('startmileage').value);
//       let endmileage = (document.getElementById('endmileage').value);
//       let costpermile = parseFloat(document.getElementById('costpermile').value);
      
//       let distance = endmileage - startmileage;
//       let mileage = distance * costpermile;
  
//      document.getElementById('outputDiv').innerHTML = mileage;
//       // console.log(mileage)
//     }
    // calculate()
let startmileage = 0;
let endmileage = 0;
let costpermile = 0;
let reimbursement = 0;

function calculate() {
const distance = endmileage - startmileage;
reimbursement = distance * costpermile;
}


</script>


    <!-- <div>
        <button type="button" on:click={calculate}>Calculate Amount</button>
    </div>
    <br>
    <div>
        <h3>Amount Reimbursed</h3><div id="outputDiv"></div>
    </div> -->

<div>
    <label for="startmileage">Start Mileage:</label>
    <input type="number" id="startmileage" bind:value={startmileage} />
    
    <label for="endmileage">End Mileage:</label>
    <input type="number" id="endmileage" bind:value={endmileage} />
    
    <label for="costpermile">Cost Per Mile:</label>
    <input type="number" id="costpermile" bind:value={costpermile} />
    
    <button on:click={calculate}>Calculate</button>
    </div>
    
    <div id="outputDiv">
    <p>Mileage: {reimbursement}</p>
    </div>