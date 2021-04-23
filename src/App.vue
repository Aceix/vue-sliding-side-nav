<template>
  <StackedSideNavLayout />
</template>

<script>
import StackedSideNavLayout from './layout/StackedSideNavLayout.vue'

export default {
  name: 'App',
  components: {
    StackedSideNavLayout
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
html, body {
  padding: 0px;
  margin: 0px;
}
</style>
