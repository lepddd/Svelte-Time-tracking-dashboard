<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import perfil from "/image-jeremy.png";

  export let selectedPeriod: string = "";

  let periods = ["Daily", "Weekly", "Monthly"];

  const dispatch = createEventDispatcher();

  const changePeriod = (period: string) => {
    dispatch("changePeriod", period);
  };
</script>

<div class="card">
  <div class="container">
    <div class="img_box">
      <img class="img" src={perfil} alt="" />
    </div>

    <div class="user_detail">
      <p class="title">Report for</p>
      <p class="username">Jeremy Robson</p>
    </div>
  </div>

  <div class="card_list">
    {#each periods as period (period)}
      <button
        class:active={period === selectedPeriod}
        on:click={() => changePeriod(period)}>{period}</button
      >
    {/each}
  </div>
</div>

<style>
  .container {
    background-color: hsl(246, 80%, 60%);
    padding: 30px;
    border-radius: 12px;
    height: 70%;
  }
  .card {
    grid-area: 1 / 1 / 3 / 2;
    height: 100%;
    width: 230px;
    background-color: hsl(235, 46%, 20%);
    border-radius: 12px;
  }
  .img_box {
    margin-bottom: 26px;
    padding: 2px;
    background-color: #f4f4f4;
    border-radius: 50%;
    width: 80px;
    height: 80px;
  }
  .img {
    width: 100%;
    height: 100%;
  }
  .title {
    color: hsl(236, 100%, 87%);
    font-size: 0.875rem;
  }
  .username {
    font-size: 32px;
    color: #f4f4f4;
    font-weight: 300;
  }

  .card_list {
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 30%;
    display: flex;
    padding: 0 30px;
    gap: 16px;
  }

  button {
    font-size: 1rem;
    background-color: hsl(235, 46%, 20%);
    border: 1px solid hsl(235, 46%, 20%);
    text-align: start;
    color: hsl(235, 45%, 61%);
    cursor: pointer;
  }

  button:hover {
    color: #f4f4f4;
  }

  button.active {
    color: #f4f4f4;
  }

  @media screen and (max-width: 1084px) {
    .card {
      width: 100%;
      grid-area: 1 / 1 / 2 / 4;
    }
    .container {
      display: flex;
      align-items: center;
      gap: 30px;
    }
    .card_list {
      flex-direction: row;
      justify-content: space-around;
      padding: 12px;
    }
    .img_box {
      margin-bottom: 0;
    }
  }

  @media screen and (max-width: 810px) {
    .card {
      width: 320px;
    }
    .card_list {
      flex-direction: row;
      justify-content: space-around;
      padding: 12px;
    }
    .container {
      height: fit-content;
      gap: 20px;
    }
    .img_box {
      width: 60px;
      height: 60px;
    }
    .username {
      font-size: 24px;
      color: #f4f4f4;
      font-weight: 300;
    }
  }
</style>
