<script>
// @ts-nocheck

  import { onMount} from "svelte"
  import Display from './components/Display.svelte'
  import Form from './components/Form.svelte'
  import Header from './components/Header.svelte'
  import Footer from './components/Footer.svelte'

  const url="https://mileagetrackerbackend-ag.onrender.com/trips"

  // state 
  let showForm = false
  let tripname = ""
  let tripdate = ""
  let startmileage = ""
  let endmileage = ""
  let costpermile = ""
  let reimbursement = ""
  let id = ""
  let trips = []
  let action = "create"

  // functions
  const getTrips = async () => {
    const response = await fetch (url)
    const data = await response.json()
    trips = data
  }

  const toggleForm = () => {
    showForm = !showForm
  }

  const resetState = () => {
    showForm = false
    tripname = ""
    tripdate = ""
    startmileage = ""
    endmileage = ""
    costpermile = ""
    reimbursement = ""
    id = ""
    action = "create"
    getTrips()
  }

  const createTrips = async (trip) => {
    await fetch(url, {
      method: "post",
      headers: {
        "Content-Type":"application/json"
      },
      body: JSON.stringify(trip)
    })

    resetState() 
  }

  const selectTripUpdate = (trip) => {
    tripname = trip.tripname
    tripdate = trip.tripdate
    startmileage = trip.startmileage
    endmileage = trip.endmileage
    costpermile = trip.costpermile
    reimbursement = trip.reimbursement
    id = trip.id
    action = "update"
    showForm = true
  }

  const updateTrips = async (trip) => {
    await fetch(url + `/${trip.id}`, {
      method: "put",
      headers: {
        "Content-Type":"application/json"
      },
      body: JSON.stringify(trip)
    })

    resetState() 
  }

  const deleteTrips = async (trip) => {
    await fetch(url + `/${trip.id}`, {
      method: "delete",
    })
    resetState() 
  }

// Lifecycle
onMount (() => {getTrips()})
</script>

<Header />

<main>
  <button class="createButton" on:click={toggleForm}>Create a new Trip</button>
  <h1>Trips Made</h1>
  <Display 
  trips={trips} 
  select={selectTripUpdate} 
  destroy={deleteTrips}
  />
  {#if showForm}
  <Form 
    tripname = {tripname}
    tripdate = {tripdate}
    startmileage = {startmileage}
    endmileage = {endmileage}
    costpermile = {costpermile}
    reimbursement = {reimbursement}
    id = {id}
    action = {action}
    create = {createTrips}
    update = {updateTrips}
  />
  {/if}
</main>

 <Footer />

<style>
  main{
    max-width: 960px;
    margin: 40px auto;
  }

  .createButton {
    padding: 10px;
  }

   h1 {
    color: white;
    text-shadow:2px 2px #000;
   }
</style>
