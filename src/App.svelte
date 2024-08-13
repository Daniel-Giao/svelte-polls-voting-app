<script>
  // stores import
  import PollStore from "./stores/PollStore";

  // components import
  import Header from "./components/Header.svelte";
  import Footer from "./components/Footer.svelte";
  import Tabs from "./shared/Tabs.svelte";
  import PollList from "./components/PollList.svelte";
  import CreatePollForm from "./components/CreatePollForm.svelte";

  // tabs
  let items = ["Current Polls", "Add New Poll"];
  let activeItem = "Current Polls";
  const tabChange = (e) => {
    activeItem = e.detail;
  };

  const handleAddNewPoll = (e) => {
    activeItem = "Current Polls";
  };
</script>

<Header />
<main>
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
  {#if activeItem === "Current Polls"}
    {#if $PollStore.length > 0}
      <p class="instruction">Click on poll's bar to vote</p>
    {:else}
      <p class="instruction">There are no polls at the moment. Try adding a new one :)</p>
    {/if}
    <PollList />
  {:else if activeItem === "Add New Poll"}
    <CreatePollForm on:addNewPoll={handleAddNewPoll} />
  {/if}
</main>
<Footer />

<style>
  .instruction {
    color: #707070;
    margin: 40px auto;
    text-align: center;
  }
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
