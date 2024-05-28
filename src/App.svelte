<script>
  import Tile from "./components/Tile.svelte";
</script>

<main>
  <h1>Pixel Pop</h1>
  <div class="tiles">
    <Tile />
    <Tile />
    <Tile />
  </div>
  <div class="score-bar">
    
  </div>
  <button>Start</button>
  <h3>Leaderboard</h3>
  <div class="leaderboard">
    <ol>
      <li>Michael</li>
      <li>Peter</li>
      <li>Jason</li>
      <li>Marty</li>
      <li>Alice</li>
    </ol>
  </div>
</main>

<style>
  h1 {
    font-size: 3.2em;
    line-height: 1.1;
    color: orangered;
  }
  .tiles {
    display: flex;
    justify-content: center;
  }
  button {
    margin-top: 4em;
    height: 4em;
    width: 13em;
    border-radius: 10px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    font-family: inherit;
    color: #fff;
    background: orangered;
    cursor: pointer;
    transition: border-color 0.25s;
  }
  .score-bar {
    height: 1em;
    width: 80%;
    background: rgb(48, 48, 48);
    border-radius: 10px;
    margin: 2em auto;
  }
  h3 {
    margin-top: 3em;
    letter-spacing: 10px;
    font-size: 25px;
    color: orangered;
  }
  ol {
    display: inline-block;
    text-align: left;
    margin-top: 0px;
    color: orangered;
  }
  li {
    margin: 1em;
    letter-spacing: 5px;
    font-size: 20px;
  }
</style>
