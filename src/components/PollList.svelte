<script>
  // stores import
  import PollStore from "../stores/PollStore";

  // components import
  import PollDetails from "./PollDetails.svelte";

  export let polls = [];
</script>

<div class="poll-list">
  <!-- Automatic unsub -->
  {#each $PollStore as poll (poll.id)}
    <div>
      <PollDetails {poll} />
    </div>
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>
