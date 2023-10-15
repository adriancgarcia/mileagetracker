<script>
// @ts-nocheck

  import { onMount} from "svelte"
  import Display from './components/Display.svelte'
  import Form from './components/Form.svelte'

  const url="https://mileagetrackerbackend-ag.onrender.com/trips";

  // state 
  let showForm = false
  let tripname = ""
  let tripdate = ""
  let startmileage = ""
  let endmileage = ""
  let costpermile = ""
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

// Lifecycle
onMount (() => {getTrips()})
</script>

<main>
  <h1>
    <img src="/img/vecteezy_vector-speedometer-icon_.jpg" alt="odometer">
</h1>
  <h1>Trips Made</h1>
  <button on:click={toggleForm}>Create a new Trip</button>
  <Display trips={trips} select={selectTripUpdate} />
  {#if showForm}
  <Form 
    tripname = {tripname}
    tripdate = {tripdate}
    startmileage = {startmileage}
    endmileage = {endmileage}
    costpermile = {costpermile}
    id = {id}
    action = {action}
    create = {createTrips}
    update = {updateTrips}
  />
  {/if}
</main>

<style>
  img {
        max-width: 300px;
    }
</style>
