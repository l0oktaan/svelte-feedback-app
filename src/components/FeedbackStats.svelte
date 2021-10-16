<script>
    export let count;
    export let avg;
</script>

<div class="feedback-stats">
    <h4>{count} Reviews</h4>
    <h4>Ratings Average: {avg}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>