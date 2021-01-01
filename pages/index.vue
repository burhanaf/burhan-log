<template>
<div class="posts">
  <main>
    <div class="bg-gray-100 overflow-x-hidden">
    <div class="px-6 py-8">
        <div class="flex justify-between container mx-auto">
            <div class="w-full lg:w-8/12">
                <div class="flex items-center justify-between">
                  <h1 class="text-xl font-bold text-gray-700 md:text-2xl">Post</h1>
                </div>
                <!-- here we loop through the posts -->
                  <!-- layout -->
                  <div class="post mt-6" v-for="post in posts" :key="post.id">
                      <div class="max-w-4xl px-10 py-6 bg-white rounded-lg shadow-md">
                          <div class="flex justify-between items-center"><span class="font-light text-gray-600">Jun 1,
                                  2020</span><a href="#"
                                  class="px-2 py-1 bg-gray-600 text-gray-100 font-bold rounded hover:bg-gray-500">Category</a>
                          </div>
                          <div class="mt-2"><a :href="`blog/${post.slug}`" class="text-2xl text-gray-700 font-bold hover:underline">
                            {{ post.title.rendered }}
                          </a>
                          <div v-html="post.excerpt.rendered" class="mt-2 text-gray-600"></div>
                          </div>
                          <div class="flex justify-between items-center mt-4">
                              <a :href="`blog/${post.slug}`" class="readmore text-blue-500 hover:underline">Read more ⟶</a>
                              <div><a href="#" class="flex items-center"><img
                                          src="https://images.unsplash.com/photo-1492562080023-ab3db95bfbce?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=731&amp;q=80"
                                          alt="avatar" class="mx-4 w-10 h-10 object-cover rounded-full hidden sm:block">
                                      <h1 class="text-gray-700 font-bold hover:underline">Alex John</h1>
                                  </a></div>
                          </div>
                      </div>
                  </div>
                  <!-- endlayout -->
            </div>
        </div>
    </div>
    </div>
  </main>
  </div>
</template>

<script>
export default {
computed: {
  posts() {
    return this.$store.state.posts;
  },
 },
created() {
  this.$store.dispatch("getPosts");
},
};
</script>
