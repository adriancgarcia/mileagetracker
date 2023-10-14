<script>
  import { onMount} from "svelte"
  import Display from './components/Display.svelte'
  import Form from './components/Form.svelte'

  const url="https://mileagetrackerbackend-ag.onrender.com/trips";

  // state 
  let showForm = false
  // let reminder = ""
  let completed = false
  let _id = ""
  let trips = []
  let action = "create"

  // functions
  const getTrips = async () => {
    const response = await fetch (url)
    const data = await response.json()
    trips = data
  }

// Lifecycle
onMount (() => {getTrips()})
</script>

<main>
  <h1>
    <img src="/img/vecteezy_vector-speedometer-icon_.jpg" alt="odometer">
</h1>
  <h1>Trips Made</h1>
  <Display trips={trips}/>
  {#if showForm}
  <Form />
  {/if}
</main>

<style>
  img {
        max-width: 300px;
    }
</style>
