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

    function calculate() {
    const distance = endmileage - startmileage;
    reimbursement = distance * costpermile;
    }

    
</script>


<div>
    <form on:submit={handleSubmit}>
        <div class="formTitle">
            <h2>Trip Info</h2>
        </div>
        <label for="tripname">Trip Name</label>
        <input type=text bind:value={tripname}>
        <label for="tripdate">Date of Trip</label>
        <input type=date bind:value={tripdate}>
        <label for="startmileage">Trip Beginning</label>
        <input type=number bind:value={startmileage}>
        <label for="endmileage">Trip End</label>
        <input type=number bind:value={endmileage}>
        <label for="costpermile">Cost Per Mile</label>
        <input type=number step=any bind:value={costpermile}> 
        <div class="calculate" on:click={calculate}>Calculate</div>
        <br/>
        <div id="outputDiv">
            <label for="reimbursement">Refund Amount</label>
            <input type=number step=any bind:value={reimbursement}>
        </div>

        <input type="submit" id="submit">
    </form>
</div>

<style>
    .formTitle {
        padding: 0;
        margin: 0
    }
    form{
        width: 300px;
        margin: 0 auto;
        padding:  20px;
        text-align: center;
        border: 3px solid white;
        border-radius: 6px;
        background-color: black;
        opacity: 0.7;
    }

    
    input{
        width: 80%;
        border-radius: 6px;
        text-align: center;
        margin: 10px;
        padding: 10px;
        color: black;
        font-size:1em;
    }
    label{
        margin: 10px;
        text-align: left;
        color: white;
        padding: 10px 0 15px 0;
    }

    #outputDiv {
    width: 100%;
    height: 10px;
    margin: 0 auto;
    text-align: center;
    padding: 5px 0 5px 0;
    font-size: 16px;
    color: black;
    border: 1px solid black;
    }

    /* button{
      margin-top: 20px;
      border: 1px solid black;
    } */

    .calculate {
        background-color: white;
        color: black;
        border-radius: 6px;
        height: 35px;
        width: 75%;
        padding-top: 10px;
        text-align: center;
        margin: 25px 0 0 38px;     
    }

    .calculate:hover {
        cursor: pointer;
    }

    #submit {
        margin: 0;
        margin-top: 90px;
    }

    #submit:hover {
        cursor: pointer;
    }

    h2 {
        color: white;
    }
  </style>