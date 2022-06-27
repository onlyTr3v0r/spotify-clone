<script lang="ts">
  export let val = 0;
  export let width;
  export let max;

  let hovered = false;
  let handle_clicked = false;
  let wrapper: HTMLElement;
  $: sliderWidth = (val / max) * 100 + "%";

  function mouseMove(evt: MouseEvent) {
    if (handle_clicked) {
      let width_num = width.replace(/\D/g,'');
      console.log(width_num);
      let dist = Math.min(
        Math.max(evt.clientX - wrapper.getBoundingClientRect().left, 0),
        width_num
      );
      let perc = dist / wrapper.offsetWidth;
      val = max * perc;
    }
  }
</script>

<svelte:body
  on:mousemove={(evt) => mouseMove(evt)}
  on:mouseup={() => (handle_clicked = false)} />

<div id="content">
    <div id="wrapper" bind:this={wrapper} style="--max-width: {width}">
      <div
        id="slider"
        style="--slider-width: {sliderWidth}"
        on:mouseenter={() => (hovered = true)}
        on:mouseleave={() => (hovered = false)}
      >
        {#if hovered}
          <div id="handle" on:mousedown={() => (handle_clicked = true)} />
        {/if}
      </div>
    </div>
</div>

<style lang="scss">
  $height: 5px;

  #slider {
    height: 100%;
    width: var(--slider-width);

    background-color: white;
    border-radius: 10px;

    display: flex;
    align-items: center;
  }

  #wrapper {
    width: var(--max-width);
    background-color: gray;
    border-radius: 10px;
    height: $height;
  }

  #slider:hover,
  #slider:active {
    background-color: #1db954;
  }

  #handle {
    margin-left: auto;
    height: $height + 5px;
    width: $height + 5px;

    background-color: white;
    border-radius: 10px;
  }
</style>
