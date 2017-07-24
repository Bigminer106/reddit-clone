<template>
  <div class="well well-lg" id="wellgroup">
    <!-- <div class="well well-lg">
      <label for="name-input">Name</label>
      <input type="text" name="name-input" id="name-input">
      <label for="username-input">Username</label>
      <input type="text" name="username-input" id="username">
      <label for="url-input">URL</label>
      <input type="text" name="url-input" id="url">
      <button>CLICK ME</button>
    </div> -->
    <div class="well well-lg" id="posts">
      <h1 v-for="name in names">{{ names.name }}</h1>
      <h2 v-for="username in names">{{ names.username }}</h2>
      <h3 v-for="url in names">{{ names.url }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'well',
  data: {
    names: [
      {
        name: 'Adam',
        username: 'Bigminer106',
        url: 'miner.adam1@hotmail.com'
      },
      {
        name: 'Will',
        username: 'Kelaintheglass',
        url: 'miner.adam1@hotmail.com'
      },
      {
        name: 'Marlena',
        username: 'SnekMomma',
        url: 'miner.adam1@hotmail.com'
      },
      {
        name: 'Michael',
        username: 'BalagnalikeLasagna',
        url: 'miner.adam1@hotmail.com'
      }
    ]
  }
}
</script>

<style>
</style>
