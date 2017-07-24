<template>
  <div id="app">
    <navigation></navigation>
    <well></well>
    <posts></posts>
  </div>
</template>
<script>
import navigation from './components/navigation'
import well from './components/wellGroup'
import posts from './components/Posts'
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
