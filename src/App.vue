<template>
<div id="app">

  <nav class="navbar navbar-default">
    <div class="container">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
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
          <div class="form-group" v-bind:class="{ 'has-error': blur.emptyTitle && isEmpty(newPost.title) }">
            <label for="title">Title</label>
            <input type="text" id="title" class="form-control" v-model="newPost.title" v-on:blur="blur.emptyTitle = true">
          </div>
          <div class="form-group" v-bind:class="{ 'has-error': blur.emptyBody && isEmpty(newPost.body) }">
            <label for="body">Body</label>
            <textarea type="text" id="body" class="form-control" v-model="newPost.body" v-on:blur="blur.emptyBody = true"></textarea>
          </div>
          <div class="form-group"  v-bind:class="{ 'has-error': blur.emptyAuthor && isEmpty(newPost.author) }">
            <label for="author">Author</label>
            <input type="text" id="author" class="form-control" v-model="newPost.author" v-on:blur="blur.emptyAuthor = true">
          </div>
          <div class="form-group"  v-bind:class="{ 'has-error': blur.emptyImage && isEmpty(newPost.image) }">
            <label for="image-url">Image URL</label>
            <input type="url" id="image-url" class="form-control" v-model="newPost.image" v-on:blur="blur.emptyImage = true">
          </div>
          <div class="form-group">
            <button type="button" class="btn btn-primary" v-on:click="submitForm()">
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
            <img v-bind:src="post.image" class="media-object">
          </div>
          <div class="media-body">
            <h4 class="media-heading">
              {{post.title}}
              <a><i class="glyphicon glyphicon-arrow-up" v-on:click="post.value++"></i></a>
              <a><i class="glyphicon glyphicon-arrow-down" v-on:click="post.value > 0 ? post.value-- : post.value"></i></a>
              Votes: {{post.value}}
            </h4>
            <div class="text-right">
              {{post.author}}
            </div>
            <p>
              {{post.body}}
            </p>
            <div>
               <!-- Time since Post | -->
              <i class="glyphicon glyphicon-comment"></i>
              <a v-on:click="showComments">{{commentNumber()}}</a>
            </div>
            <div class="row" v-for="comment in comments">
              <div class="col-md-offset-1" v-show="commentsShown">
                <hr>
                <h4>{{comment.commentAuthor}}</h4>
                <p>{{comment.comment}}</p>
                <div>
                  <p><a class="btn btn-info" v-on:click="newCommentAdd" v-show="addComment">Add Comment</a></p>
                </div>
                <form class="form-inline" v-show="commentOpened">
                  <div class="form-group">
                    <label for="#commentAuthor">Author:</label>
                    <input class="form-control" id="commentAuthor" v-model="newComment.commentAuthor">
                  </div>
                  <div class="form-group">
                    <label for="#comment">Comment:</label>
                    <input class="form-control" id="comment" v-model="newComment.comment">
                  </div>
                  <div class="form-group">
                    <button type="button" class="btn btn-primary" v-on:click="submitComment">Submit</button>
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
      posts: [
        {
          title: 'Slipsum',
          author: 'S.L. Jackson',
          image: "https://lorempixel.com/100/100/",
          body: "Now that we know who you are, I know who I am. I'm not a mistake! It all makes sense! In a comic, you know how you can tell who the arch-villain's going to be? He's the exact opposite of the hero. And most times they're friends, like you and me! I should've known way back when... You know why, David? Because of the kids. They called me Mr Glass.",
          value: 0
        },
        {
          title: 'Slipsum',
          author: 'S.L. Jackson',
          image: "https://lorempixel.com/100/100/",
          body: "You think water moves fast? You should see ice. It moves like it has a mind. Like it knows it killed the world once and got a taste for murder. After the avalanche, it took us a week to climb out. Now, I don't know exactly when we turned on each other, but I know that seven of us survived the slide... and only five made it out. Now we took an oath, that I'm breaking now. We said we'd say it was the snow that killed the other two, but it wasn't. Nature is lethal but it doesn't hold a candle to man.",
          value: 2
        },
        {
          title: 'Slipsum',
          author: 'S.L. Jackson',
          image: "https://lorempixel.com/100/100/",
          body: "Well, the way they make shows is, they make one show. That show's called a pilot. Then they show that show to the people who make shows, and on the strength of that one show they decide if they're going to make more shows. Some pilots get picked and become television programs. Some don't, become nothing. She starred in one of the ones that became nothing.",
          value: 4
        }
      ],
      newPost: {
        title: '',
        author: '',
        image: '',
        body: '',
        value: 0
      },
      blur: {
        emptyTitle: false,
        emptyBody: false,
        emptyAuthor: false,
        emptyImage: false
      },
      comments: [
        {
          commentAuthor: 'RandoJS',
          comment: 'FIRST'
        }
      ],
      newComment: {
        commentAuthor: '',
        comment: ''
      },
      commentOpened: false,
      addComment: true,
      commentsShown: false
    }
  },
  methods: {
    // Toggles the form to add a post
    toggleForm() {
      if (this.opened == false) {
        this.opened = true;
      } else {
        this.opened = false;
      }
    },
    isEmpty(value) {
      return value === '';
    },
    submitForm() {
      if (this.blur.emptyTitle == true || this.blur.emptyBody == true || this.blur.emptyAuthor == true || this.blur.emptyImage == true) {
        event.preventDefault();
        alert("All fields required.");
      } else {
        this.blur.title = false;
        this.blur.body = false;
        this.blur.author = false;
        this.blur.image = false;
        this.posts.push(this.newPost);
        this.toggleForm();
      }
    },
    newCommentAdd() {
      if (this.commentOpened == false) {
        this.commentOpened = true;
      } else {
        this.commentOpened = false;
      };
      if (this.addComment == true) {
        this.addComment = false;
      } else {
        this.addComment = true;
      };
    },
    submitComment() {
      this.comments.push(this.newComment);
      this.newCommentAdd();
    },
    commentNumber() {
      if (this.comments.length === 1) {
        return this.comments.length + ' comment';
      } else {
        return this.comments.length + ' comments';
      };
    },
    showComments() {
      if (this.commentsShown == false) {
        this.commentsShown = true;
      } else {
        this.commentsShown = false;
      };
    }
  }
}

</script>

<style>
</style>
