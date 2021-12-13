<template>
  <div class="phone-body">
    <div class="feed" v-if="step === 1">
      <vuegram-post
        v-for="post in posts"
        :post="post"
        :key="posts.indexOf(post)"
      />
    </div>
  </div>
</template>

<script>
import vuegramPost from "./VuegramPost.vue";
export default {
  name: "PhoneBody",
  props: {
    step: Number,
    posts: Array,
    filters: Array,
  },
  components: {
    "vuegram-post": vuegramPost,
  },
};
</script>

<style lang="scss" src="../styles/phone-body.scss"></style>
