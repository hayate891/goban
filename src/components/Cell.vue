<template>
  <div class="cell">
    <div class="piece" :class="color(state.color)" v-on:click="play">
      <div v-if="state.active" class="active"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'cell',
  props: ['state', 'cur-move'],
  methods: {
    color: function (intColor) {
      switch (intColor) {
        case -1:
          return 'white'

        case 0:
          return 'empty'

        case 1:
          return 'black'
      }
    },
    play: function () {
      this.state.color = this.curMove
      this.$emit('play')
    }
  }
}
</script>

<style lang="scss">
  .cell {
    width: 90%;
    height: 90%;
    position: absolute;
    left: -50%;
    top: -50%;
    margin-left: 1px;
    margin-top: 1px;
    z-index: 10;

    .piece {
      display: block;
      width: 100%;
      height: 100%;
      border-radius: 100%;

      &.black {
        background: #333;
        pointer-events: none;
      }

      &.white {
        background: #f1f1f1;
        pointer-events: none;
      }

      &.empty {
        cursor: pointer;

         &:hover {
          .black & {
            background: rgba(#333, 0.5);
          }

          .white & {
            background: rgba(#f1f1f1, 0.5);
          }
        }
      }
    }

    .active {
      display: block;
      width: 40%;
      height: 40%;
      border-radius: 100%;
      position: absolute;
      left: 30%;
      top: 30%;
      margin-left: -3px;
      margin-top: -3px;
    }

    .black .active {
      border: 3px solid #f1f1f1;
    }

    .white .active {
      border: 3px solid #333;
    }
  }
</style>
