<template>
  <div
    class="vue-hamb-menu noselect"
    :style="{color: color}"
  >
    <div
      v-if="open"
      class="menu-back"
      :class="{halfOpacity: darken}"
    />
    <div
      v-if="position === 'right'"
      class="menu-icon-right menu-icon-container"
      @click="toggleMenu"
    >
      <i class="material-icons menu-icon">menu</i>
    </div>

    <div
      v-if="position === 'left'"
      class="menu-icon-left menu-icon-container"
    >
      <i class="material-icons menu-icon">menu</i>
    </div>
  </div>
</template>

<script>

  // add positioning values - horizontal, vertical

export default {
  name: 'VueHambMenu',
  data() {
    return ({
      open: false,
    })
  },
  props: {
    color: {
      type: String,
      required: false,
      default: '#000'
    },
    position: {
      type: String,
      required: false,
      default: 'right'
    },
    darken: {
      type: Boolean,
      required: false,
      default: false,
    }
  },
  methods: {
    toggleMenu() {
      this.open = !this.open;
    }
  }
}
</script>

<style>

.vue-hamb-menu {
  overflow: hidden;
}

.menu-icon {
  font-size: 50px;
}

.menu-icon-container {
  position: fixed;
  top: 10px;
  cursor: pointer;
}

.menu-icon-right {
  right: 20px;
}

.menu-icon-left {
  left: 20px;
}

.menu-back {
  position: fixed;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  background-color: #000;
  opacity: 0;
}

.halfOpacity {
  opacity: 0.5;
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
}

</style>
