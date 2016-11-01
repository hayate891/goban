<template>
  <div class="board" :class="{ black: curMove === 1, white: curMove === -1 }">
    <table>
      <tbody>
        <tr v-for="col in state.grid">
          <td v-for="cell in col">
            <Cell :state="cell" :cur-move="curMove" v-on:play="play"></Cell>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Cell from './Cell'

export default {
  name: 'board',
  props: ['state'],
  components: {
    Cell
  },
  data: () => {
    return {
      curMove: 1
    }
  },
  methods: {
    play: function () {
      this.curMove *= -1
    }
  }
}
</script>

<style lang="scss">
  $blah: 'hello';
  
  .board {
    padding: 40px;
    padding-right: 0;
    padding-bottom: 0;
    background: #fbcb65;
    display: inline-block;
    table {
      border-collapse: collapse;

    }
    tr:last-child {
      td {
        border-right: none;
        border-bottom: none;
        border-left: none;
      }
    }

    %marker {
      $size: 7px;
      content: " ";
      display: block;
      width: $size;
      height: $size;
      background: #333;
      left: - ceil($size/2);
      top: - ceil($size/2);
      border-radius: 100%;
      position: absolute;
    }

    tr:nth-child(3), tr:nth-child(7), tr:nth-child(5) {
      td:nth-child(3), td:nth-child(7), td:nth-child(5) {
        &:before {
          @extend %marker;
        }
      }
    }

    tr:nth-child(5) td:nth-child(5) {
      &:before {
        @extend %marker;
      }
    }

    td {
      width: 40px;
      height: 40px;
      position: relative;
      border: 1px solid #333;

      &:last-child {
        border-top: none;
        border-right: none;
        border-bottom: none;
      }
    }
  }
</style>
