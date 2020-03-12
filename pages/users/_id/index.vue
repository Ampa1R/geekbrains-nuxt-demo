<template>
  <div>
      <h4>User posts</h4>
      <section>
            <div class="post" v-for="post in posts" :key="post.id">
                <p><strong>{{ post.title }}</strong></p>
                <p>{{ post.body }}</p>
            </div>
      </section>
  </div>
</template>

<script>
export default {
    async asyncData(context) {
        const res = await fetch(`https://jsonplaceholder.typicode.com/users/${context.route.params.id}/posts`);
        const posts = await res.json();
        return {
            posts
        };
    },
}
</script>

<style scope>
.post {
    border: 1px solid #ccc;
    margin-bottom: 10px;
    padding: 5px;
}
</style>