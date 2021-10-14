<script>
    import FeedbackItem from "./FeedbackItem.svelte";
    export let feedBack = []

    console.log(feedBack)
</script>

{#each feedBack as fb (fb.id)}
    <FeedbackItem item={fb} on:delete-feedback />
{/each}