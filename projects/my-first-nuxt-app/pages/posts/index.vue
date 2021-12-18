<template>
  <div class="posts-page">
    <PostList :posts="loadedPosts" />
  </div>
</template>

<style scoped>
.posts-page {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

<script>
import PostList from "@/components/Posts/PostList";

export default {
  components: {
    PostList,
  },
  asyncData(context) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({
          loadedPosts: [
            {
              id: "1",
              title: "First Post",
              previewText: "This is our first post!",
              thumbnail:
                "https://images.unsplash.com/photo-1488590528505-98d2b5aba04b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80",
            },
            {
              id: "2",
              title: "Second Post",
              previewText: "This is our second post!",
              thumbnail:
                "https://images.unsplash.com/photo-1488590528505-98d2b5aba04b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80",
            },
          ],
        });
      }, 1500);
    })
      .then((data) => {
        return data;
      })
      .catch((e) => {
        context.error(new Error());
      });
  },
  // data() {
  //   return {
  //     loadedPosts: [],
  //   };
  // },
  created() {
    this.$store.dispatch("setPosts", this.loadedPosts);
    console.log(this.$store.getters.loadedPosts);
  },
};
</script>