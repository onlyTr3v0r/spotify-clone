<script lang="ts">
  import BarLeft from "./BarLeft.svelte";
  import BarMiddle from "./BarMiddle.svelte";
  import BarRight from "./BarRight.svelte";
</script>

<footer>
  <BarLeft/>
  <BarMiddle/>
  <BarRight/>
</footer>

<style lang="scss">
  $padding: 10px;

  footer {
    background-color: #181818;
    width: calc(100% - ($padding * 2)); // Offsetting 2* padding so it doesnt go off screen
    height: 15%;
    padding: $padding;

    position: absolute; // Place the bar at the bottom
    bottom: 0;

    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }
</style>
