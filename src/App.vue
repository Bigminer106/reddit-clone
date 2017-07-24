<template>
<div id="app">

  <nav class="navbar navbar-default">
    <div class="container">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false" v-on:click="toggleForm()">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <a class="navbar-brand">The Mine</a>
      </div>
      <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
      </div>
    </div>
  </nav>

  <main class="container">

    <div class="pull-right">
      <p><a class="btn btn-info" v-on:click="toggleForm()">New Post</a></p>
    </div>

    <ul class="nav nav-pills">
      <li role="presentation" class="active">
        <input type="search" class="form-control input-sm search-form" placeholder="Filter">
      </li>
      <div class="form-inline">
        <label for="sort">  Sort by </label>
        <select class="form-control" id="sort">
          <option>Oldest</option>
          <option>Most Recent</option>
          <option>Title(A-Z)</option>
          <option>Title(Z-A)</option>
        </select>
      </div>
    </ul>
    
    <div class="row" v-show="opened">
      <div class="col-md-8">

        <form>
          <div>
            <label for="title">Title</label>
            <input id="title" class="form-control">
          </div>
          <div>
            <label for="body">Body</label>
            <textarea id="body" class="form-control"></textarea>
          </div>
          <div>
            <label for="author">Author</label>
            <input id="author" class="form-control">
          </div>
          <div>
            <label for="image-url">Image URL</label>
            <input id="image-url" class="form-control">
          </div>
          <div class="form-group">
            <button type="submit" class="btn btn-primary" v-on:click="addPost()">
              Create Post
            </button>
          </div>
        </form>

      </div>
    </div>
    <h2>News from the Shaft</h2>
    <div class="row">
      <div class="col-md-12">

        <div class="well" v-for='post in posts'>
          <div class="media-left">
            <img src="" class="media-object" alt="lorempixel Crap">
          </div>
          <div class="media-body">
            <h4 class="media-heading">
              {{post.title}}
              <a><i class="glyphicon glyphicon-arrow-up" v-on:click="votesUp()"></i></a>
              <a><i class="glyphicon glyphicon-arrow-down" v-on:click="votesDown()"></i></a>
              Votes: {{value}}
            </h4>
            <div class="text-right">
              {{post.author}}
            </div>
            <p>
              {{post.body}}
            </p>
            <div>
              Some time ago |
              <i class="glyphicon glyphicon-comment"></i>
              <a>
                Some comments
              </a>
            </div>
            <div class="row">
              <div class="col-md-offset-1">
                <hr>
                <p>
                  Comment text
                </p>
                <form class="form-inline">
                  <div class="form-group">
                    <input class="form-control">
                  </div>
                  <div class="form-group">
                    <input type="submit" class="btn btn-primary">
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>

  </main>
  Contact GitHub
</div>
</template>

<script>
export default {
  el: '#app',
  data() {
    return {
      opened: false,
      value: 0,
      posts: [
        {
          title: 'Slipsum',
          author: 'S.L. Jackson',
          // image: "https://lorempixel.com/200/400/",
          body: "Now that we know who you are, I know who I am. I'm not a mistake! It all makes sense! In a comic, you know how you can tell who the arch-villain's going to be? He's the exact opposite of the hero. And most times they're friends, like you and me! I should've known way back when... You know why, David? Because of the kids. They called me Mr Glass."
        },
        {
          title: 'Slipsum',
          author: 'S.L. Jackson',
          // image: "https://lorempixel.com/200/400/",
          body: "You think water moves fast? You should see ice. It moves like it has a mind. Like it knows it killed the world once and got a taste for murder. After the avalanche, it took us a week to climb out. Now, I don't know exactly when we turned on each other, but I know that seven of us survived the slide... and only five made it out. Now we took an oath, that I'm breaking now. We said we'd say it was the snow that killed the other two, but it wasn't. Nature is lethal but it doesn't hold a candle to man."
        },
        {
          title: 'Slipsum',
          author: 'S.L. Jackson',
          // image: "https://lorempixel.com/200/400/",
          body: "Well, the way they make shows is, they make one show. That show's called a pilot. Then they show that show to the people who make shows, and on the strength of that one show they decide if they're going to make more shows. Some pilots get picked and become television programs. Some don't, become nothing. She starred in one of the ones that became nothing."
        }
      ]
    }
  },
  methods: {
    toggleForm() {
      if (this.opened == false) {
        this.opened = true;
      } else {
        this.opened = false;
      }
    },
    votesUp() {
      if (this.value >= 0) {
        this.value++;
      };
    },
    votesDown() {
      if (this.value > 0) {
        this.value--;
      } else {
        alert("Can't have less than 0 votes!");
      };
    },
    addPost() {

    }
  }
}
</script>

<style>
</style>
