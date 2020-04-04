<script>
  import Row from "./Row.svelte";
  import data from "./data";

  let query = "";
  let priceVariant = "normal";
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
    <span>Tipo de precio</span>
    <select bind:value={priceVariant}>
      <option value="normal">Normal</option>
      <option value="night">Noche</option>
      <option value="flick">Kamilo</option>
      <option value="cj">CJ</option>
    </select>
  </label>
</div>

<div class="list-container">
  {#each filtered as item}
    <Row {...item} {priceVariant} />
  {/each}
</div>
