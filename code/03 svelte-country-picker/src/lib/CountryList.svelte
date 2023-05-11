<script>
    import {createEventDispatcher} from "svelte";

    export let countries;

    const dispatch = createEventDispatcher()
    const selectCountry = name => {
        dispatch('selected', {name})
    }
</script>

<!--UI-->
<div>
    <ul class="list-group">
        {#each countries as country}
            <li class="list-group-item"
                on:click={()=>selectCountry(country.name)}>
                <img src={country.flag} alt="" class="imgFlag">
                <h4>{country.name}</h4>
                <p>{country.capital}</p>
            </li>
        {/each}
    </ul>
</div>
