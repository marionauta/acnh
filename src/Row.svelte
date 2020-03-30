<script>
  export let type;
  export let name;
  export let price;
  export let comment;
  export let priceType;

  let renderPrice;
  $: if (priceType === "night") {
    renderPrice = price * 0.8;
  } else if (priceType === "flick" && type === "insect") {
    renderPrice = price * 1.5;
  } else {
    renderPrice = price;
  }
</script>

<style>
  .container {
    padding: 1rem;
  }

  .insect {
    font-weight: bold;
  }

  .container:nth-child(2n) {
    background: #efefef;
  }

  .topRow {
    display: flex;
    justify-content: space-between;
  }

  .comment {
    border-top: 1px dashed #efefef;
    padding-top: 0.5rem;
    margin-top: 0.5rem;
  }
</style>

<div
  class="container"
  class:insect={priceType === 'flick' && type === 'insect'}>
  <div class="topRow">
    <span>{name}</span>
    <span>{renderPrice}</span>
  </div>
  {#if comment}
    <div class="comment">{comment}</div>
  {/if}
</div>
