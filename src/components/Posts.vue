<template lang="html">
  <div id="posts">
    <h3>News from the Shaft</h3>
    <div class="well well-lg">
      <div v-for="post in posts">
        <div>
          <h2>{{post.title}}</h2>
        </div>
      </div>
      <!-- posts append here, then add votes in it -->

    </div>
  </div>
</template>

<script>
export default {
  name: 'posts',
  data() {
    return {
      posts: [
        {
          title: 'Man struggles to survive in apocalyptic scenario',
          body: 'Lorem ipsum',
          image: 'http://lorempixel.com/200/400/',
          votes: 0
        },
        {
          title: 'Goody-goody gets gulped by giant',
          body: 'Lorem ipsum',
          image: 'http://lorempixel.com/200/400/',
          votes: 6
        },
        {
          title: 'Man awarded Darwin award posthumously',
          body: 'Lorem ipsum',
          image: 'http://lorempixel.com/200/400/',
          votes: 20
        }
      ]
    }
  }
}
</script>

<style lang="css">
#votes {
  width: 5%
}
</style>
