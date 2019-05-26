<template>
  <div :class="$style.root">
    <app-control
        :isHide="src"
        @change="changeFileHandler"
    />
    <video
        v-if="src"
        :src="src"
        :class="$style.player"
        controls
    />
  </div>
</template>

<script>
  import AppControl from './AppControl';

  export default {
    name: "AppPlayer",
    components: { AppControl },
    data() {
      return {
        src: null,
      }
    },
    methods: {
      changeFileHandler(value) {
        this.src = value;
      }
    }
  }
</script>

<style lang="scss" module>
  .root {
    position: relative;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
  }

  .player {
    object-fit: contain;
    width:100%;
    height:100%;
  }
</style>
