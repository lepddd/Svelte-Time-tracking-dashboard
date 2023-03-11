<script lang="ts">
  import ellipsis from "../assets/icon-ellipsis.svg";

  interface Props {
    title: string;
    timeframes: {
      daily: {
        current: number;
        previous: number;
      };
      monthly: {
        current: number;
        previous: number;
      };
      weekly: {
        current: number;
        previous: number;
      };
    };
  }

  export let track: Props;
  export let selectedPeriod: string;

  let iconSrc = track.title.split(" ").join("-");
  let cardClass = track.title.split(" ").join("_").toLowerCase();

  $: ({ title, timeframes } = track);
</script>

<div class="card {cardClass}">
  <img class="icon" src="../src/assets/icon-{iconSrc}.svg" alt="icon" />
  <section class="details">
    <div class="details_top">
      <p class="details_title">{title}</p>
      <img src={ellipsis} alt="icon" />
    </div>
    <p class="time">
      {timeframes[selectedPeriod.toLowerCase()].current}hrs
    </p>
    {#if selectedPeriod === "Daily"}
      <p class="resume">
        Last Day - {timeframes[selectedPeriod.toLowerCase()].previous}hrs
      </p>
    {:else if selectedPeriod === "Weekly"}
      <p class="resume">
        Last Week - {timeframes[selectedPeriod.toLowerCase()].previous}hrs
      </p>
    {:else}
      <p class="resume">
        Last Month - {timeframes[selectedPeriod.toLowerCase()].previous}hrs
      </p>
    {/if}
  </section>
</div>

<style>
  .card {
    position: relative;
    overflow: hidden;
    border-radius: 12px;
    padding-top: 36px;
    z-index: 0;
    width: 230px;
    height: 100%;
  }
  .details {
    display: flex;
    flex-direction: column;
    border-radius: 12px;
    gap: 10px;
    padding: 30px;
    background-color: hsl(235, 46%, 20%);
  }
  .details_top {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .details_title {
    font-size: 18px;
    color: #f4f4f4;
  }
  .time {
    font-size: 48px;
    color: #f4f4f4;
    font-weight: 300;
  }
  .resume {
    color: hsl(235, 45%, 61%);
    font-size: 0.75rem;
  }
  .icon {
    position: absolute;
    top: -8px;
    right: 10px;
    z-index: -1;
    width: 64px;
    height: 64px;
  }
  .work {
    background: linear-gradient(
      180deg,
      hsl(15, 100%, 70%) 50%,
      hsl(235, 46%, 20%) 50%
    );
  }
  .play {
    background: linear-gradient(
      180deg,
      hsl(195, 74%, 62%) 50%,
      hsl(235, 46%, 20%) 50%
    );
  }
  .study {
    background: linear-gradient(
      180deg,
      hsl(348, 100%, 68%) 50%,
      hsl(235, 46%, 20%) 50%
    );
  }
  .exercise {
    background: linear-gradient(
      180deg,
      hsl(145, 58%, 55%) 50%,
      hsl(235, 46%, 20%) 50%
    );
  }
  .social {
    background: linear-gradient(
      180deg,
      hsl(264, 64%, 52%) 50%,
      hsl(235, 46%, 20%) 50%
    );
  }
  .self_care {
    background: linear-gradient(
      180deg,
      hsl(43, 84%, 65%) 50%,
      hsl(235, 46%, 20%) 50%
    );
  }
</style>
