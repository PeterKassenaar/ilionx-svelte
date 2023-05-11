<script lang="ts">
    // define interface - ideally of course in its own file
    import CustomerDetail from "./CustomerDetail.svelte";

    interface Customer {
        id: number;
        name: string;
        city: string;
    }

    // Define array of data
    let customers: Customer[] = [
        {id: 1, name: 'KPN', city: 'Amsterdam'},
        {id: 2, name: 'Belastingdienst', city: 'Apeldoorn'},
        {id: 3, name: 'Ilionx', city: 'Maastricht'},
        {id: 4, name: 'Rabobank', city: 'Utrecht'},
    ]

    let custName
</script>
<!--Below: all HTML. It MIGHT be in a div, but it is not mandatory-->
<h2>List of Customers</h2>
<ul>
    {#each customers as customer}
        <li on:click={()=>{custName = customer.name}}>{customer.id} - {customer.name}</li>
    {/each}
</ul>
<!--Show customer name, but only if one is clicked-->
<!--{#if custName}-->
<!--    <CustomerDetail name={custName}/>-->
<!--{/if}-->
