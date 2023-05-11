<script lang="ts">
  let count: number = 0
  const increment = () => {
    count +=1
  }

  const decrement = ()=>{
    count -=1
  }

  const reset =()=>{
    count = 0
  }

  const update = val =>{
    count +=val
  }
  let value;
</script>

<button on:click={increment}>Increment</button>
<button on:click={decrement}>decrement</button>
<button on:click={reset}>reset</button>
<!--Reading values from a text field-->
<!--<input type="number" placeholder="value..."-->
<!--       bind:value-->
<!--       on:keyup={e => e.key==='Enter' && update(value)} >-->

<h2>count is {count}</h2>
