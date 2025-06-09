<template>
  <div id="app">
    <ComponentContainer/>
  </div>
</template>

<script>
import ComponentContainer from './components/ComponentContainer.vue'

export default {
  name: 'App',
  components: {
    ComponentContainer
  }
}
</script>

<style>
body{
  margin: 0;
}
</style>
