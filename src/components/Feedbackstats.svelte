<script>
  import { FeedBackStore } from "../store";

  $: count = $FeedBackStore.length;
  $: average =
    $FeedBackStore.reduce((acc, { rating }) => acc + rating, 0) / count;
</script>

<div class="feedback-stats">
  <h4>{count} Reviews</h4>
  <h4>Ratings average {average}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
