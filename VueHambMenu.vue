<template>
  <div
    class="vue-hamb-menu"
    :style="{color: color}"
  >
    <div
      v-if="position === 'right'"
      class="menu-icon-right menu-icon-container"
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
export default {
  name: 'VueHambMenu',
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
    }
  }
}
</script>

<style>

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

</style>
