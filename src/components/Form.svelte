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
        <input type=date id="tripdate" bind:value={tripdate}>
        <label for="startmileage">Trip Start</label>
        <input type=number bind:value={startmileage}>
        <label for="endmileage">Trip End</label>
        <input type=number bind:value={endmileage}>
        <label for="costpermile">Cost Per Mile</label>
        <input type=number step=any bind:value={costpermile}> 
        <div id="calculate" on:click={calculate}>Calculate</div>
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

    form {
        width: 300px;
        margin: 0 auto;
        padding:  20px;
        text-align: center;
        border: 3px solid white;
        border-radius: 6px;
        background-color: rgba(0, 0, 0, .8);
    }

    input {
        width: 80%;
        border-radius: 6px;
        text-align: center;
        margin: 10px;
        padding: 10px;
        color: black;
        font-size:1em;
        background-color: white;
    }

    #tripdate {
        width: 80%;
        border-radius: 6px;
        text-align: center;
        margin: 10px;
        padding: 10px;
        color: black;
        font-size:1em;
        background-color: white;
    }

    label {
        margin: 10px;
        text-align: left;
        color: white;
        padding: 10px 0 15px 0;
    }

    #outputDiv {
        margin-top: 15px;
    }

    #calculate {
        border-radius: 6px;
        height: 35px;
        width: 75%;
        padding-top: 5px;
        text-align: center;
        margin: 25px 0 10px 0;  
        display:inline-block;
        box-sizing: border-box;
        text-decoration:none;
        font-family:'Roboto',sans-serif;
        text-transform:uppercase;
        font-weight:400;
        color:#FFFFFF;
        background-color:#3369ff;
        box-shadow:inset 0 -0.6em 0 -0.35em rgba(0,0,0,0.17);
}
    #calculate:active {
            top:0.1em;
    }
    @media all and (max-width:30em) {
        #calculate{
            display:block;
            margin:0.4em auto;
            }
    }

    #calculate:hover {
        cursor: pointer;
    }

    #submit {
        margin: 0;
        margin-top: 40px;
        display:inline-block;
        box-sizing: border-box;
        text-decoration:none;
        font-family:'Roboto',sans-serif;
        text-transform:uppercase;
        font-weight:400;
        color:#FFFFFF;
        background-color:#3369ff;
        box-shadow:inset 0 -0.6em 0 -0.35em rgba(0,0,0,0.17);
}
    #submit:active{
            top:0.1em;
    }
    @media all and (max-width:30em){
        #submit{
            display:block;
            margin:0.4em auto;
            }
    }

    #submit:hover {
        cursor: pointer;
    }

    h2 {
        color: white;
    }

    @media screen and (max-width: 600px) { 
    #tripdate {
        width: 200%;
        border-radius: 6px;
        text-align: center;
        margin: 10px;
        padding: 10px 20px 10px 20px;
        color: black;
        font-size:1em;
        background-color: blue;
    }
}
  </style>