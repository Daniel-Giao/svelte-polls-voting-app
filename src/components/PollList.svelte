<script>
  // transition & animate imports
  import { fade, slide, scale } from "svelte/transition";
  import { flip } from "svelte/animate";

  // stores import
  import PollStore from "../stores/PollStore";

  // components import
  import PollDetails from "./PollDetails.svelte";
</script>

<div class="poll-list">
  <!-- Automatic unsub -->
  {#each $PollStore as poll (poll.id)}
    <div in:fade out:scale|local animate:flip={{ duration: 500 }}>
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
