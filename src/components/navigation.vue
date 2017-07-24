<template>
  <div id="navigation">
    <nav class="navbar-default">
      <div class="container-fluid">
        <div class="navbar-header">
          <h1><a href="#" class="return">The Mine</a></h1><br>
          <!-- Move the button right -->
          <button type="button" name="Add Post" class="btn" v-on:click="toggleForm()">Add Post</button><br><br>
          <div v-show="opened">
            <h3>This is the form</h3>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'navigation',
  data() {
    return {
      opened: false
    }
  },
  methods: {
    toggleForm() {
      if (this.opened == false) {
        this.opened = true;
      } else {
        this.opened = false;
      }
    }
  }
}
</script>

<style>
h1 {
  text-decoration: underline;
}
</style>
