<template>
  <div id="wellgroup">
    <!-- Move this form to a modal or something -->
    <div class="well well-lg">
      <label for="username-input">Username</label>
      <input type="text" name="username-input" id="username">
      <label for="password-input">Password</label>
      <input type="text" name="password-input" id="url">
      <button>Login</button>
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
        password: 'dummyPW1'
      },
      {
        name: 'Will',
        username: 'Kelaintheglass',
        url: 'dummyPW2'
      },
      {
        name: 'Marlena',
        username: 'SnekMomma',
        url: 'dummyPW3'
      },
      {
        name: 'Michael',
        username: 'BalagnalikeLasagna',
        url: 'dummyPW4'
      }
    ]
  }
}
</script>

<style>
</style>
