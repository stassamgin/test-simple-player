<template>
  <div
      :class="$style.root"
      @mouseover="isHover = true"
      @mouseout="isHover = false"
  >
    <div
        :class="[$style.panel,{[$style.hide]: isHide}, {[$style.hover]: isHover}]"
        ref="panel"
    >
      <input type="file" @change="changeFileHandler"/>
      <button @click="clearFileHandler">Clear</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "AppControl",
    props: {
      isHide: {
        type: Boolean,
      },
    },
    data() {
      return {
        isHover: false,
      }
    },
    methods: {
      changeFileHandler(e) {
        this.$emit('change', URL.createObjectURL(e.target.files[0]));
      },

      clearFileHandler() {
        this.$emit('change', null);
      }
    },
  }
</script>

<style lang="scss" module>
  .root {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
  }

  .panel {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: white;
    padding: 10px 20px;
    margin-bottom: 20px;
  }

  .hide {
    transform: translateY(-100%);
    transition: all 0.3s;
  }

  .hover {
    transform: translateY(0);
  }
</style>
