<template>
  <div class="phone-body">
    <div class="feed" v-if="step === 1">
      <vuegram-post
        v-for="post in posts"
        :post="post"
        :key="posts.indexOf(post)"
      />
    </div>

    <div v-if="step === 2">
      <div
        class="selected-image"
        :class="selectedFilter"
        :style="{ backgroundImage: 'url(' + image + ')' }"
      ></div>

      <div class="filter-container">
        <filter-type
          v-for="filter in filters"
          :filter="filter"
          :image="image"
          :key="filters.indexOf(filter)"
        ></filter-type>
      </div>
    </div>
  </div>
</template>

<script>
import vuegramPost from "./VuegramPost.vue";
import FilterType from "./FilterTypes.vue";
export default {
  name: "PhoneBody",
  props: {
    step: Number,
    posts: Array,
    filters: Array,
    image: String,
    selectedFilter: String,
  },
  components: {
    "vuegram-post": vuegramPost,
    "filter-type": FilterType,
  },
};
</script>

<style lang="scss" src="../styles/phone-body.scss"></style>
