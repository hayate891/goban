<template>
  <div class="board">
    <table>
      <tbody>
        <tr v-for="col in state.grid">
          <td v-for="cell in col" class="cell">
            <div class="cell">
              <div 
                class="piece" 
                :class="{ empty: cell.color === 0, black: cell.color === 1, white: cell.color === -1 }"
                v-on:click="curMove *= -1; cell.color = curMove"
              ></div>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'board',
  props: ['state'],
  data: () => {
    return {
      curMove: 1
    }
  }
}
</script>

<style lang="scss">
  $blah: 'hello';

  

  .piece {
    width: 90%;
    height: 90%;
    border-radius: 100%;
    position: absolute;
    left: -50%;
    top: -50%;
    margin-left: 1px;
    margin-top: 1px;
    z-index: 10;
    
    &.black {
      background: #333;
      // cursor: pointer;
    }

    &.white {
      background: #f1f1f1;
      // cursor: pointer;
    }

    &.empty {
      cursor: pointer;
    }
  }

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

  // table {
  //  border-collapse: collapse;
  //  border: none;
  //  border-spacing: 0;

  //  tr {
  //    &:first-child {
  //      td {
  //        &:after {
  //          height: 50%;
  //          top: 50%;
  //        }
  //      }
  //    }

  //    &:last-child {
  //      td {
  //        &:after {
  //          height: 50%;
  //          bottom: 50%;
  //        }
  //      }
  //    }

  //    td {
  //      &:first-child {
  //        &:before {
  //          width: 50%;
  //          left: 50%;
  //        }
  //      }

  //      &:last-child {
  //        &:before {
  //          width: 50%;
  //          right: 50%;
  //        }
  //      }
  //    }
  //  }

  //  td {
  //    width: 30px;
  //    height: 30px;
  //    border: none;

  //    position: relative;

  //    &:after {
  //      content: " ";
  //      display: block;
  //      position: absolute;
  //      width: 1px;
  //      height: 100%;
  //      left: 50%;
  //      top: 0;
  //      background: #333;
  //    }

  //    &:before {
  //      content: " ";
  //      display: block;
  //      position: absolute;
  //      width: 100%;
  //      height: 1px;
  //      left: 0;
  //      top: 50%;
  //      background: #333;
  //    }
  //  }
  // }
</style>
