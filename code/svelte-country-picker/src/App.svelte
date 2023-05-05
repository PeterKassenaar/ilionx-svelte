<script>
  // 0. variables/state in application
  // TODO: Utilize TypeScript with lang="ts" and define interfaces etc!
  import axios from "axios";
  import CountryList from "./lib/CountryList.svelte";
  import CountryDetail from "./lib/CountryDetail.svelte";

  const url = 'https://restcountries.com/v2/name/';
  const fields = '?fields=name,capital,flag';
  let countryName = '';
  let countries = [];
  let selectedCountry = '';

  // 1. Methods/Functions
  // 1a. Search for specific country
  const search = async () => {
    console.log('search for:: ', countryName);
    countries = await axios.get(`${url}${countryName}${fields}`)
            .then(res => res.data);
    console.log(countries);
  }

  // 2. reset
  const clear = () => {
    selectedCountry = '';
    countryName = '';
    countries = [];
  }

  // 3. Get details for country
  const getDetails = async (event) => {
    console.log('Search details for: ', event.detail.name);
    selectedCountry = await axios.get(`${url}${event.detail.name}`)
            .then(res => res.data[0]);
  }
</script>

<!--User interface. See index.html, where we load Bootstrap.
    CSS-file is bundled in main.ts -->
<main class="container">
  <div class="row">
    <div class="col-6">
      <h1>Svelte Country Picker!</h1>
      <input type="text"
             bind:value={countryName}
             on:keyup={ e => e.key==='Enter' && search()}
             placeholder="search country..."
             class="form-control-lg"/>
      <button on:click={search} class="btn btn-primary">Search</button>
      <button on:click={clear} class="btn btn-info">Clear</button>
      <hr>
    </div>
  </div>
  <!--	Second row-->

  <div class="row">
    <div class="col-6">
<!--      Using Svelte if-statement. We use countries as prop for the component-->
      {#if countries.length > 0}
        <h2>Found countries</h2>
        <CountryList countries={countries} on:selected={e =>getDetails(e)}/>
      {/if}
    </div>
    <div class="col-6">
      {#if selectedCountry}
        <CountryDetail country={selectedCountry}/>
      {/if}
    </div>
  </div>
</main>
