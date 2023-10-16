<script>
    export let tripname
    export let tripdate
    export let startmileage
    export let endmileage
    export let costpermile
    export let reimbursement
    export let id
    export let action 
    export let create 
    export let update
    // export let calculate

    // function calculate() {
    //   let startmileage = parseFloat(document.getElementById('startmileage').value);
    //   let endmileage = parseFloat(document.getElementById('endmileage').value);
    //   let costpermile = parseFloat(document.getElementById('costpermile').value);
      
    //   let distance = endmileage - startmileage;
    //   let mileage = distance * costpermile;
  
    //   document.getElementById('outputDiv').innerHTML = mileage;
    
    // }

    const handleSubmit = (event) => {
        event.preventDefault()
        if(action === "create"){
            create({
                tripname, 
                tripdate, 
                startmileage, 
                endmileage, 
                costpermile,
                reimbursement
            })
        }
        if(action === "update"){
            update({
                id, 
                tripname, 
                tripdate, 
                startmileage, 
                endmileage, 
                costpermile,
                reimbursement
            })
        }
    }

    // let startmileage = 0;
    // let endmileage = 0;
    // let costpermile = 0;
    // let mileage = 0;

    function calculate() {
    const distance = endmileage - startmileage;
    reimbursement = distance * costpermile;
    }

    
</script>


<div>
<form on:submit={handleSubmit}>
    <div class="formTitle">
        <h2>My Trips</h2>
      </div>
    <label for="tripname">Trip Name</label>
    <input type=text bind:value={tripname}>
    <label for="tripdate">Date of Trip</label>
    <input type=date bind:value={tripdate}>
    <label for="startmileage">Trip Beginning</label>
    <input type=number bind:value={startmileage}>
    <label for="endmileage">Trip End</label>
    <input type=number bind:value={endmileage}>
    <label for="costPerMile">Cost Per Mile</label>
    <input type=number step=any bind:value={costpermile}> 
    <div>
        <button on:click={calculate}>Calculate</button>
    </div>
    
    <div id="outputDiv">
    <p>Mileage: {reimbursement}</p>
    </div>
    <input type=submit>
</form>
    
</div>

<style>
    .formTitle {
      padding: 0;
      margin: 0
    }
    form{
          width: 350px;
          margin: 0 auto;
          padding:  0 50px 0 30px;
          text-align: center;
          border: 3px solid black;
          border-radius: 6px;
      }
  
      
      input{
          width: 100%;
          border-radius: 6px;
          text-align: left;
          padding: 10px;
      }
      label{
          margin: 10px auto;
          text-align: left;
      }
      #outputDiv {
      width: 40%;
      height: 10px;
      margin: 0 auto;
      text-align: center;
      padding: 5px 0 20px 0;
      font-size: 16px;
      color: black;
      border: 1px solid black;
    }
    button{
      margin: 20px;
      border: 1px solid black;
    }
  </style>