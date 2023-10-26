<script>
import ButtonCounterView from "./ButtonCounterView.vue";
import BlogPost from "./BlogPost.vue";

export default {
  components: {
    ButtonCounterView,
    BlogPost,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "제목1" },
        { id: 2, title: "제목2" },
        { id: 3, title: "제목3" },
      ],
      postFontSize: 1,
    };
  },
};
</script>

<template>
  <div class="layout">
    <h1>This is component page</h1>
    <ButtonCounterView />
    <ButtonCounterView />
    <br />
    <h2>blog</h2>
    <div :style="{ fontSize: postFontSize + 'em' }">
      <BlogPost
        v-for="post in posts"
        :key="post.id"
        :title="post.title"
        @enlarge-text="postFontSize += 0.1"
        @smaller-text="postFontSize -= 0.1"
      />
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .layout {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
