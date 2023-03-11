<script></script>

<div class="container">
  <slot />
</div>

<style>
  .container {
    margin: 0 auto;
    width: 100%;
    min-width: 320px;
    max-width: 1024px;
    display: grid;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(2, 1fr);
    gap: 30px;
  }
</style>
