<template>
  <div id="app">
    <navigation></navigation>
    <well></well>
  </div>
</template>
<script>
import navigation from './components/navigation.vue'
import well from './components/wellGroup.vue'
export default {
  name: 'app',
  components: {
    navigation,
    well
  }
}
</script>

<style>

</style>
