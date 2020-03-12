<template>
  <div>
      <h1>User Page</h1>
      <section>
          <h3>{{ user.name }}</h3>
          <p>Website: {{ user.website }}</p>
          <p>Company: {{ user.company.name }}</p>
          <p>
              <nuxt-link :to="{ name: 'users-id', params: { id: $route.params.id } }">Posts</nuxt-link>
              <nuxt-link :to="{ name: 'users-id-todos', params: { id: $route.params.id } }">Todos</nuxt-link>
          </p>
          <nuxt-child />
      </section>
  </div>
</template>

<script>
export default {
    async asyncData(context) {
        const res = await fetch(`https://jsonplaceholder.typicode.com/users/${context.route.params.id}`);
        const user = await res.json();
        return {
            user
        };
    },
}
</script>

<style scope>
section {
    padding: 20px;
}
</style>