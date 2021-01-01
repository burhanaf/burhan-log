<template>
<main class="post individual">
  <h1>{{ post.title.rendered }}</h1>
  <section v-html="post.content.rendered"></section>
</main>
</template>


<script>
import axios from "axios"
let dynamicRoutes = () => {
return axios
  .get("https://css-tricks.com/wp-json/wp/v2/posts?page=1&per_page=20")
  .then(res => {
    return res.data.map(post => `/blog/${post.slug}`)
  })
}

export default {
computed: {
  posts() {
    return this.$store.state.posts;
  },
  post() {
    return this.posts.find(el => el.slug === this.slug);
  }
},
data() {
  return {
    slug: this.$route.params.slug
  };
},
created() {
  this.$store.dispatch("getPosts");
}
};
</script>
