<template>
  <div class="container">
    <h1>Welcome to the forum</h1>
    <ThreadList :threads="threads"/>
  </div>
</template>
<script>
import sourceData from "@/data";
import ThreadList from "./ThreadList";
console.log(sourceData);
export default {
  components: {
    ThreadList
  },
  data() {
    return {
      threads: Object.values(sourceData.threads),
      posts: sourceData.posts,
      users: sourceData.users
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  text-align: center;
}
.container {
  margin: auto;
}

.posts-container {
  background-color: white;
  display: flex;

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
