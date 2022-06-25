<script lang="ts">
  export let favourited: boolean = false;
  let hovered = false;
  $: strokecolour = favourited ? "#1ED760" : (hovered ? "#E5E5E5" : "#bababa");
  $: fillcolour = favourited ? "#1ED760" : "none"

  function toggle() {
    favourited = !favourited;
  }
</script>

<div id="icon"
    on:click={toggle}
    on:mouseenter={() => hovered = true}
    on:mouseleave={() => hovered = false}
>
    <svg width="41.111" height="40.508" version="1.1" viewBox="0 0 10.877 10.718" xmlns="http://www.w3.org/2000/svg">
        <!-- Created with Inkscape (http://www.inkscape.org/) -->
        <g transform="translate(-11.454 -8.1936)">
        <path d="m16.893 10.558s-3.1109-4.2044-4.77-0.32052c-1.6591 3.8839 4.77 8.2769 4.77 8.2769m-1e-6 -7.9564s3.1109-4.2044 4.77-0.32052c1.6591 3.8839-4.77 8.2769-4.77 8.2769" fill={fillcolour} stroke={strokecolour} stroke-linecap="round" stroke-width=".79375"/>
    </g>
   </svg>
</div>

<style lang="scss">
    $size: 25px;

    #icon {
        margin-left: 15px;
    }

    svg {
        width: $size;
        height: $size;
    }
</style>