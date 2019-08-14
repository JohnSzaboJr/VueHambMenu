<template>
  <div
    class="vue-hamb-menu noselect"
    :style="{color: iconColor}"
  >
    <div
      v-if="slideOut"
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
      :style="{backgroundColor: menuColor,
              color: linkColor}"
      :class="{menuSlideoutLeft: position === 'left',
              menuSlideoutRight: position === 'right',
              openRight: position === 'right' && slideOut,
              openLeft: position === 'left' && slideOut}"
    >
      <div
        class="close-icon-container noselect"
        @click="toggleMenu"
        :class="{closeIconRight: position === 'right',
                closeIconLeft: position === 'left'}"
      >
        <i class="material-icons close-icon">close</i>
      </div>
      <div
        class="menu-links"
      >
        <div
          class="menu-link"
          v-for="link in links"
          :key="link.text"
          :style="{fontSize: linkSize + 'px',
                  marginBottom: linkSpacing + 'px'}"
        >
          <a :href="link.href">{{ link.text }}</a>
        </div>
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
      slideOut: false,
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
    links: {
      type: Array,
      required: false,
      default: [],
    },
    linkSize: {
      type: Number,
      required: false,
      default: 18
    },
    linkSpacing: {
      type: Number,
      required: false,
      default: 40
    }, 
  },
  methods: {
    toggleMenu() {
      if (this.open) {
        this.slideOut = false;
        setTimeout(() => {
          this.open = false;
        }, 300);
      } else {
        this.open = true;
        setTimeout(() => {
          this.slideOut = true;
        }, 1);
      }
    }
  }
}
</script>

<style scoped>

a {
  color: #fff;
  text-decoration: none;
}

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

.menu-links {
  position: absolute;
  margin-top: 90px;
  margin-left: 45px;
}

.menu-slideout {
  width: 300px;
  position: fixed;
  top: 0px;
  bottom: 0px;
}

.menuSlideoutRight {
  right: -300px;
  transition: right 300ms;
}

.menuSlideoutLeft {
  left: -300px;
  transition: left 300ms;
}

.openRight {
  right: 0px;
}

.openLeft {
  left: 0px;
}

.close-icon-container {
  position: absolute;
  margin: 10px;
  cursor: pointer;
}

.closeIconRight {
  left: 0px;
}

.closeIconLeft {
  right: 0px;
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
