<script lang="ts">
  import ControlBar from "./components/ControlBar.svelte";
  import AlbumCover from "./components/AlbumCover.svelte";
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&display=swap" rel="stylesheet">
</svelte:head>

<ControlBar/>
<AlbumCover/>

<style lang="scss">
  :root {
    font-family: Inter, sans-serif;
    height: 100%;
  }

  :global(body) {
    margin: 0;
    height: 100%;
  }
</style>
