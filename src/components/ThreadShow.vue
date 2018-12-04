<template>
  <div class="container">
    <div class="threads-container">
      <h2>{{ thread.title}}</h2>
      <div
        class="posts-container"
        v-for="postId in thread.posts"
        v-bind:key="postId"
      >
        <div class="user-info">
          <div class="user-info-name">
            <a href="#">{{users[posts[postId].userId].name}}</a>
          </div>
          <div class="user-info-avatar">
            <img v-bind:src="users[posts[postId].userId].avatar" />
          </div>

        </div>
        <div class="post-info">
          {{posts[postId].text}}
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import sourceData from "@/data";

export default {
  props: {
    id: {
      required: true,
      type: String
    }
  },
  data() {
    return {
      thread: sourceData.threads[this.id],
      posts: sourceData.posts,
      users: sourceData.users
    };
  }
};
</script>

<style scoped>
.container {
  width: 800px;
  margin: auto;
}

.posts-container {
  background-color: white;
  display:flex;

  border-radius: 5px;
  margin-bottom: 5px;
}
.user-info {
  text-align: center;
  width: 120px;
  flex: none;
  margin-right: auto;
}
.user-info-name {
  display: block;
  margin: 10px;
}
.user-info-name > a {
  font-size: 0.8rem;
  color: #7dcea0;
  text-decoration: none;
  width: 100%;
}
.user-info-avatar {
  display: block;
  margin: auto;
}
.user-info-avatar > img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
}

.post-info {
  flex: auto;
  text-overflow: ellipsis;
  line-height: 150%;
  font-size: 0.8rem;
  text-align: left;
  padding: 10px;
}
@media screen and (max-width: 600px) {
  .col-large {
    padding: 0 10px;
  }
}
</style>
