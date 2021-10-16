<script>
	import FeedbackList from './components/FeedbackList.svelte'
	import FeedbackStats from './components/FeedbackStats.svelte'
	import FeedbackForm from './components/FeedbackForm.svelte'

	import {FeedbackStore} from './stores'
	let feedback = []

	FeedbackStore.subscribe((data) => feedback = data)

	$: count = feedback.length;
	$: avg = feedback.reduce((a,{rating}) => a + rating, 0)/feedback.length;

	const deleteFeedback = (e) => {
		const id = e.detail;
		feedback = feedback.filter((item) => item.id != id);
	}

	const addFeedback = (e) => {
		const newFeedback = e.detail
		feedback = [newFeedback,...feedback]
	}
</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback} />
	<FeedbackStats {count} {avg} />
	<FeedbackList feedback={feedback} on:delete-feedback={deleteFeedback} />
</main>

