<script>
  import Tile from "./components/Tile.svelte";
  import runGameStore from "./stores/GameRunsStore";

  let tiles = [
    {active: false},
    {active: true},
    {active: false}
  ];

  let win = 0;
  $: lose = 100 - win;

  function countScore(e) {
    if (e.detail === true) {
      win+=2;
    } else {
      win-=2;
    }

    if (win === 100) {
      finishGame();
    }

    changeActiveTile();
    console.log({win: win, lose: lose});
  }

  function changeActiveTile() {
    // Find the index of the currently active tile
    let currentIndex = tiles.findIndex(tile => tile.active);

    // Randomly select a new index, ensuring it's different from the current one
    let newIndex;
    do {
      newIndex = Math.floor(Math.random() * tiles.length);
    } while (newIndex === currentIndex);

    // Remove the active state from the current tile
    tiles[currentIndex].active = false;

    // Set the new tile as active
    tiles[newIndex].active = true;
  }

  function start() {
    runGameStore.update(store => {
      return { ...store, run: true };
    });
  }

  function finishGame() {
    runGameStore.update(store => {
      return { ...store, run: false };
    });
  }
</script>

<main>
  <h1>Pixel Pop</h1>
  <div class="tiles">
    {#each tiles as tile}
      <Tile on:activeTileClicked={countScore} {tile} />
    {/each}
  </div>

  <div class="score-bar">
    <div class="score-bar-half win" style="width: {win}%;"></div>
    <div class="score-bar-half lose" style="width: {lose}%;"></div>
  </div>

  <button on:click={start}>Start</button>
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
    color: red;
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
    letter-spacing: 2px;
    font-weight: 900;
    font-family: inherit;
    color: black;
    background: red;
    cursor: pointer;
    transition: border-color 0.25s;
  }
  .score-bar {
    display: flex;
    height: 1em;
    width: 80%;
    border-radius: 10px;
    margin: 2em auto;
    overflow: hidden; /* To ensure rounded corners are respected */
  }
  .win {
    background: red;
  }
  .lose {
    background: rgb(32, 32, 32);
  }
  h3 {
    margin-top: 3em;
    letter-spacing: 10px;
    font-size: 25px;
    color: red;
  }
  ol {
    display: inline-block;
    text-align: left;
    margin-top: 0px;
    color: red;
  }
  li {
    margin: 1em;
    letter-spacing: 5px;
    font-size: 20px;
  }
</style>
