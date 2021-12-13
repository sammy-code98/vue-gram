<template>
  <div id="app">
    <div class="app-phone">
      <div class="phone-header">
        <img
          src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/1211695/vue_gram_logo_cp.png"
        />
      </div>

      <!-- bind the posts and filters to the body as props-->
      <phone-body
        :step="step"
        :posts="posts"
        :filters="filters"
        :image="image"
        :selectedFilter="selectedFilter"
        v-model="caption"
      />
      <div class="phone-footer">
        <div class="home-cta">
          <i class="fas fa-home fa-lg"></i>
        </div>
        <div class="upload-cta">
          <input
            type="file"
            name="file"
            id="file"
            class="inputfile"
            @change="uploadImage"
          />
          <label for="file">
            <i class="far fa-plus-square fa-lg"></i>
          </label>
        </div>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
import PhoneBody from "./components/PhoneSection.vue";
import posts from "./data/posts";
import filters from "./data/filters";
export default {
  name: "App",
  data() {
    return {
      step: 1,
      posts,
      filters,
      image: "",
      selectedFilter: "",
      caption: "",
    };
  },
  components: {
    "phone-body": PhoneBody,
  },
  methods: {
    uploadImage(e) {
      const files = e.target.files;
      if (!files.length) return;
      const reader = new FileReader();
      reader.readAsDataURL(files[0]);
      reader.onload = (e) => {
        this.image = e.target.result;
        this.step = 2;

        // To enable reuploading of same files in Chrome

        document.querySelector("#file").value = "";
      };
    },
  },
};
</script>
<style lang="scss" src="./styles/app.scss"></style>
