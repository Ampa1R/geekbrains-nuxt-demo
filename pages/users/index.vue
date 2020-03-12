<template>
  <div>
      <h1>Users Page</h1>
      <section>
          <div v-for="user in users" :key="user.id" class="user">
              <nuxt-link :to="{ name: 'users-id', params: { id: user.id } }">{{ user.name }}</nuxt-link>
              <p>E-mail: {{ user.email }}</p>
              <p>Phone: {{ user.phone }}</p>
          </div>
      </section>
  </div>
</template>

<script>
export default {
    async asyncData() {
        const res = await fetch('https://jsonplaceholder.typicode.com/users');
        const users = await res.json();
        return {
            users
        };
    }
}
</script>

<style scoped>
.user {
    padding: 20px;
    box-shadow: 0 10px 10px #eee;
    margin-bottom: 20px;
}
</style>