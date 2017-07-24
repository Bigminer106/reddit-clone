<template>
  <div id="app">
    <navigation></navigation>
    <well></well>
    <posts></posts>
  </div>
</template>
<script>
import navigation from './components/navigation.vue'
import well from './components/wellGroup.vue'
import posts from './components/Posts.vue'
export default {
  name: 'app',
  components: {
    navigation,
    well,
    posts
  }
}
</script>

<style>

</style>
