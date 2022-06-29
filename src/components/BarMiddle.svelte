<script lang="ts">
  import Slider from "./Slider.svelte";

  let play = true;
  let length = "3:54";
  let time_since_begin = 0;
  let length_sec =
    Number(length.split(":")[0]) * 60 + Number(length.split(":")[1]);

  window.setInterval(function () {
    if (!play) {
      return;
    }

    if (time_since_begin + 1 >= length_sec) {
      time_since_begin = 0;
    }

    time_since_begin += 1;
    if (time_since_begin >= length_sec) {
      play = false;
    }
  }, 1000);
</script>

<div id="content">
  <div id="wrapper">
    <div id="playback-slider">
      <p>{Math.floor(time_since_begin / 60) + ":" + Math.round(time_since_begin % 60)}</p>
      <Slider max={length_sec} bind:val={time_since_begin} width="500px"/>
      <p>{length}</p>
    </div>
    <div id="playback-control">
      <button on:click={() => alert("back")} id="previous" class="track-control">
        <svg width="8.289mm" height="8.289mm" version="1.1" viewBox="0 0 8.289 8.289" xmlns="http://www.w3.org/2000/svg">
          <!-- Created with Inkscape (http://www.inkscape.org/) -->
          <circle cx="4.1445" cy="4.1445" r="4.1445" fill="#fff"/>
          <g transform="matrix(.53265 0 0 .53207 -20.813 -34.209)" stroke-width="0">
          <path transform="matrix(.63175 0 0 .62808 38.657 62.305)" d="m18.677 15.554-11.4 6.5819v-13.164z"/>
          <rect x="48.856" y="67.94" width="1.6005" height="8.2892" rx=".0020532" ry=".53194"/>
          </g>
        </svg>
      </button>
      <button on:click={() => (play = !play)} id="pause">
        {#if play}
          <svg width="8.2892mm" height="8.2892mm" version="1.1" viewBox="0 0 8.2892 8.2892" xmlns="http://www.w3.org/2000/svg">
          <!-- Created with Inkscape (http://www.inkscape.org/) -->
          <g transform="translate(-43.121 -68.077)">
          <circle cx="47.266" cy="72.222" r="4.1446" fill="#fff"/>
          <path transform="translate(-.49397 -.27006)" x="45.524422" y="70.083359" width="1.4660408" height="4.8169913" rx="0.00099546602" ry="0.22204976" d="m45.525 70.083h1.464c5.52e-4 0 9.96e-4 0.09903 9.96e-4 0.22205v4.3729c0 0.12302-4.44e-4 0.22205-9.96e-4 0.22205h-1.464c-5.51e-4 0-9.95e-4 -0.09903-9.95e-4 -0.22205v-4.3729c0-0.12302 4.44e-4 -0.22205 9.95e-4 -0.22205zm4.4692 0h-1.464c-5.52e-4 0-9.96e-4 0.09903-9.96e-4 0.22205v4.3729c0 0.12302 4.44e-4 0.22205 9.96e-4 0.22205h1.464c5.51e-4 0 9.95e-4 -0.09903 9.95e-4 -0.22205v-4.3729c0-0.12302-4.44e-4 -0.22205-9.95e-4 -0.22205z" stroke-width="0"/>
          </g>
        </svg>
        {:else}
          <svg width="8.2892mm" height="8.2892mm" version="1.1" viewBox="0 0 8.2892 8.2892" xmlns="http://www.w3.org/2000/svg">
          <!-- Created with Inkscape (http://www.inkscape.org/) -->
            <g transform="translate(-43.121 -68.077)">
            <circle cx="47.266" cy="72.222" r="4.1446" fill="#fff" stroke-width="0"/>
            <path transform="matrix(.20751 0 0 .2338 10.628 8.9488)" d="m186.02 270.63-16.566 9.5643v-19.129z" stroke="#000" stroke-linecap="round" stroke-width=".37795"/>
            </g>
          </svg>
        {/if}
      </button>
      <button on:click={() => alert("next")} class="track-control">
        <svg width="8.289mm" height="8.289mm" version="1.1" viewBox="0 0 8.289 8.289" xmlns="http://www.w3.org/2000/svg">
          <!-- Created with Inkscape (http://www.inkscape.org/) -->
          <circle cx="4.1445" cy="4.1445" r="4.1445" fill="#fff"/>
          <g transform="matrix(.53265 0 0 .53207 -20.813 -34.209)" stroke-width="0">
          <path transform="matrix(.63175 0 0 .62808 38.657 62.305)" d="m18.677 15.554-11.4 6.5819v-13.164z"/>
          <rect x="48.856" y="67.94" width="1.6005" height="8.2892" rx=".0020532" ry=".53194"/>
          </g>
        </svg>
      </button>
    </div>
  </div>
</div>

<style lang="scss">
  #content {
    display: flex;
    align-items: center;
  }

  #wrapper {
    display: grid;
    grid-template-rows: 2;
    place-items: center;
  }

  button {
    background-color: transparent;
    border: 0;

    transform-origin: 50% 50%;

    & > svg {
      width: 100%;
      height: 100%;
      transform-origin: 50% 50%;

      :hover {
        transform: scale(1.02);
      }
    }

    &:hover {
      transform: scale(1.1);
      filter: brightness(130%);
    }
  }

  p {
    color: #A7A7A7;
  }

  #playback-slider {
    grid-row: 2;
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 10px;
  }

  #playback-control {
    grid-row: 1;

    gap: 25px;
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  #pause {
    width: 75px;
    height: 75px;
  }

  #previous {
    transform: rotate(180deg);
  }

  .track-control {
    width: 50px;
    height: 50px;
  }
</style>
