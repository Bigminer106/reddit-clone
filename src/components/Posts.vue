<template lang="html">
  <div id="posts">
    <div class="well well-lg">
      <h3>News from the Shaft</h3>
      <div class="well well-lg">
        <!-- posts append here, then add votes in it -->
        <div class="well" id="votes">

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'posts'
}
</script>

<style lang="css">
#votes {
  width: 5%
}
</style>
