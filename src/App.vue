<template>
  <div id="app">
    <Board :state="state"></Board>
  </div>
</template>

<script>
import Board from './components/Board'

const BLACK = 1
const WHITE = -1
const EMPTY = 0

const grid = [
  [ { color: EMPTY }, { color: EMPTY }, { color: EMPTY }, { color: EMPTY }, { color: EMPTY } ],
  [ { color: EMPTY }, { color: BLACK }, { color: WHITE }, { color: EMPTY }, { color: EMPTY } ],
  [ { color: EMPTY }, { color: WHITE, active: true }, { color: BLACK }, { color: EMPTY }, { color: EMPTY } ],
  [ { color: EMPTY }, { color: EMPTY }, { color: WHITE }, { color: BLACK }, { color: EMPTY } ],
  [ { color: EMPTY }, { color: EMPTY }, { color: EMPTY }, { color: EMPTY }, { color: EMPTY } ]
]

export default {
  name: 'app',
  components: {
    Board
  },
  data: () => {
    return {
      state: {
        rows: grid.length,
        cols: grid[0].length,
        grid
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
