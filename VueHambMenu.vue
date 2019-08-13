<template>
  <div
    class="vue-hamb-menu noselect"
    :style="{color: iconColor}"
  >
    <div
      v-if="open"
      class="menu-back"
      :class="{halfOpacity: darken}"
      @click="toggleMenu"
    />

    <div
      v-if="position === 'right'"
      class="menu-icon-right menu-icon-container"
      :style="{top: vertical + 'px', right: horizontal + 'px'}"
      @click="toggleMenu"
    >
      <i class="material-icons menu-icon">menu</i>
    </div>

    <div
      v-if="position === 'left'"
      class="menu-icon-left menu-icon-container"
      :style="{top: vertical + 'px', left: horizontal + 'px'}"
      @click="toggleMenu"
    >
      <i class="material-icons menu-icon">menu</i>
    </div>
    
    <div 
      v-if="open"
      class="menu-slideout"
      :style="{backgroundColor: menuColor}"
      :class="{menuSlideoutLeft: position === 'left',
              menuSlideoutRight: position === 'right'}"
    >
      <div
        class="close-icon-container"
        @click="toggleMenu"
        :style="{color: linkColor}"
        :class="{menuSlideoutLeft: position === 'right',
                menuSlideoutRight: position === 'left'}"
      >
        <i class="material-icons close-icon">close</i>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'VueHambMenu',
  data() {
    return ({
      open: false,
    })
  },
  props: {
    iconColor: {
      type: String,
      required: false,
      default: '#000'
    },
    linkColor: {
      type: String,
      required: false,
      default: '#fff'
    },
    menuColor: {
      type: String,
      required: false,
      default: '#292929'
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
    },
    horizontal: {
      type: Number,
      required: false,
      default: 20
    },
    vertical: {
      type: Number,
      required: false,
      default: 10
    },
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

.menu-slideout {
  width: 300px;
  position: fixed;
  top: 0px;
  bottom: 0px;
}

.menuSlideoutRight {
  right: 0px;
}

.menuSlideoutLeft {
  left: 0px;
}

.close-icon-container {
  position: absolute;
  margin: 10px;
  cursor: pointer;
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
