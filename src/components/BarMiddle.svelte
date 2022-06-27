<script lang="ts">
  import Slider from "./Slider.svelte";

  let play = true;
  // let length = "3:54";
  let length = "0:10";
  let time_since_begin = 0;
  let length_sec =
    Number(length.split(":")[0]) * 60 + Number(length.split(":")[1]);

  window.setInterval(function () {
    if (!play) {
      return;
    }

    time_since_begin += 1;
    if (time_since_begin >= length_sec) {
      play = false;
    }
  }, 1000);
</script>

<div id="content">
  <div id="wrapper">
    <Slider max={length_sec} bind:val={time_since_begin} width="500px"/>
    <button on:click={() => (play = !play)}>Click</button>
    <p>{time_since_begin}</p>
  </div>
</div>

<style lang="scss">
  button {
    width: 50px;
    height: 50px;
  }

  p {
    color: white;
  }

  #content {
    padding: 25px;
    display: flex;
    align-items: center;
  }
</style>
