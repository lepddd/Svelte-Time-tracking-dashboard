<script lang="ts">
  import Card from "./lib/Card.svelte";
  import data from "./data/data.json";
  import Container from "./lib/Container.svelte";
  import ProfileCard from "./lib/ProfileCard.svelte";

  let selectedPeriod = "Daily";

  const changePeriod = (e: CustomEvent) => {
    selectedPeriod = e.detail;
  };
</script>

<main>
  <Container>
    <ProfileCard on:changePeriod={changePeriod} {selectedPeriod} />
    {#each data as track}
      <Card {track} {selectedPeriod} />
    {/each}
  </Container>
</main>

<style>
  main {
    width: 100%;
  }
</style>
