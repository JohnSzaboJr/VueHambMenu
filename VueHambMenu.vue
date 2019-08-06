<template>
  <div class="vue-hamb-menu">
    <div class="menu-icon-container">
      <i class="material-icons menu-icon">menu</i>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VueHambMenu',
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
