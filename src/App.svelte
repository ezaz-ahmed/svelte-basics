<script>
  import FeedbackForm from "./components/FeedbackForm.svelte";

  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/Feedbackstats.svelte";

  let feedBack = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 3,
      rating: 8,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
  ];

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedBack = feedBack.filter((fb) => fb.id !== itemId);
  };

  $: count = feedBack.length;
  $: average = feedBack.reduce((prev, { rating }) => prev + rating, 0) / count;

  const doTask = (ev) => {
    feedBack = [...feedBack, ev.detail];
  };
</script>

<main class="container">
  <FeedbackForm on:add-new-feedback={doTask} />
  <FeedbackStats {count} {average} />
  <FeedbackList {feedBack} on:delete-feedback={deleteFeedback} />
</main>

<style>
</style>
