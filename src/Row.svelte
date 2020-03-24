<script>
  export let name;
  export let price;
  export let comment;
  export let showNight;
</script>

<style>
  .container {
    padding: 1rem;
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

<div class="container">
  <div class="topRow">
    <span>{name}</span>
    <span>{showNight ? price * 0.8 : price}</span>
  </div>
  {#if comment}
    <div class="comment">{comment}</div>
  {/if}
</div>
