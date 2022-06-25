<script lang="ts">
  import HeartButton from "./HeartButton.svelte";

  let name = "On Melancholy Hill";
  let artist = "Gorillaz";
</script>

<div id="content">
    <div> <!-- This div is centered with flexbox but the text isnt. -->
        <a href="/"><p id="name">{name}</p></a>
        <a href="/"><p id="artist">{artist}</p></a>
    </div>
    <HeartButton/>
</div>

<style lang="scss">
  #content {
    display: flex;
    align-items: center;
  }

  #name {
    font-weight: bold;
    color: #F3F3F3;
  }

  #artist {
    color: #9B9B9B;
    display: inline; // So the border-bottom propery works properly
  }

  p {
    margin: 5px;
  }

  a {
    text-decoration: none;

    :hover {
        border-bottom: 1px solid white;
    }
  }
</style>