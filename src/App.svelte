<script>
  import Row from "./Row.svelte";
  import data from "./data";

  let query = "";
  let showNight = false;
  $: filtered = data.filter(
    item => !query || item.name.toLowerCase().includes(query.toLowerCase())
  );
</script>

<style>
  .list-container {
    border: 1px solid #efefef;
    border-radius: 2px;
    margin: 1rem;
    margin-top: 0;
  }

  .searchbar {
    position: sticky;
    top: 0;
    padding: 1rem;
    background-color: #fff;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>

<div class="searchbar">
  <input type="text" placeholder="Buscar..." bind:value={query} />
  <label>
    <input type="checkbox" bind:checked={showNight} />
    <span>Precios nocturnos</span>
  </label>
</div>

<div class="list-container">
  {#each filtered as { name, price, comment }}
    <Row {name} {price} {comment} {showNight} />
  {/each}
</div>
