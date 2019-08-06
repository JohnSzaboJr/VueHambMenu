<template>
  <div class="vue-hamb-menu">
    <div
      class="menu-icon-container"
      :style="{color: color}"
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
    }
  }
}
</script>

<style>

.menu-icon {
  font-size: 50px;
}

.menu-icon-container {
  position: absolute;
  right: 20px;
  top: 10px;
  cursor: pointer;
}

</style>
