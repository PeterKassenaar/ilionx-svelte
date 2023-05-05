<script>
    // View component for country details
    export let country;
</script>

<!--UI-->

<div>
    <h2>Details for {country.name}</h2>
</div>
<ul class="list-group">
    <li class="list-group-item">
        <img class="countryFlag"
             style="max-width: 100%"
             src={country.flag} alt="Flag for {country.name}">
    </li>
    <li class="list-group-item">
        <strong>{country.name}</strong>
        (native: <strong>{country.nativeName}</strong>)
    </li>
    <li class="list-group-item">
        Capital: <strong>{country.capital}</strong>
    </li>
    <li class="list-group-item">
        Population: <strong>{country.population}</strong>
    </li>
    <li class="list-group-item">
        Region: <strong>{country.region} / {country.subregion}</strong>
    </li>
    <li class="list-group-item">
        Top-level internet domain: <strong>{ country.topLevelDomain }</strong>
    </li>
</ul>
