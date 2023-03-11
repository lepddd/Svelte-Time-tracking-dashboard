<script></script>

<div class="container">
  <slot />
</div>

<style>
  .container {
    margin: 0 auto;
    min-width: fit-content;
    max-width: 1024px;
    display: grid;
    grid-template-columns: repeat(4, 230px);
    grid-template-rows: repeat(2, 1fr);
    gap: 30px;
  }

  @media screen and (max-width: 1084px) {
    .container {
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(3, 1fr);
    }
  }

  @media screen and (max-width: 810px) {
    .container {
      flex-direction: column;
      display: flex;
      gap: 20px;
    }
  }
</style>
