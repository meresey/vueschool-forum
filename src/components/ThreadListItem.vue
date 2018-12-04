<template>
  <div class="container">
    <div class="col-1">
      <div class="thread-title">

        <router-link :to="`/thread/${thread['.key']}`">{{ thread.title}}</router-link>
      </div>
      <div class="thread-details">
        <span class="by">By</span><span class="author"> {{user.name}}</span>
        <span class="timestamp">, {{ thread.publishedAt}}</span>
      </div>
    </div>

    <div class="col-2">
      <div class="replies">
        <span>{{repliesCount}} replies</span>
      </div>
      <div class="avatar">
        <img
          :src="user.avatar"
          alt=""
        >
      </div>
    </div>
    <!-- <div
      class="threads-container"
      v-for="thread in threads"
      v-bind:key="thread.threadId"
    > -->

    <!-- <div
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

      </div> -->
    <!-- </div> -->
  </div>
</template>

<script>
import sourceData from '@/data'
export default {
  props: {
    thread: {
      required: true,
      type: Object
    }
  },
  data() {
    return {
      users: sourceData.users
    }
  },
  computed: {
    repliesCount() {
      return Object.keys(this.thread.posts).length - 1
    },
    user() {
      return this.users[this.thread.userId]
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  width: 100%;

  padding: 5px 0 5px 15px;
}
.container:nth-child(odd) {
  background-color: white;
  border-radius: 0 0 0 20px;
  background-color: #f2f3f4;
}
.col-1 {
  flex: none;
  width: 400px;
}
.col-2 {
  flex: auto;
}

.thread-title > a {
  font-weight: 550;
  font-size: 0.8rem;
  margin: 5px 0;
  display: block;
  color: #28B463;
  text-decoration: none;
}
.thread-title > a:hover {
  opacity: 0.5;
}
.author {
  color: #28B463;
}
.author,
.by,
.timestamp,
.replies {
  font-size: 0.7rem;
}
.replies, .avatar {
  display: inline-block;
  text-align: center;
  width: 50px;
  margin: auto;
}

.avatar > img {
  width: 20px;
  height: 20px;
  border-radius: 50%;
}
</style>
