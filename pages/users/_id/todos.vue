<template>
  <div>
      <h4>User todos</h4>
      <section>
            <div :class="['todo', {'todo--completed': todo.completed}]" v-for="todo in todos" :key="todo.id">
                {{ todo.title }}
            </div>
      </section>
  </div>
</template>

<script>
export default {
    async asyncData(context) {
        const res = await fetch(`https://jsonplaceholder.typicode.com/users/${context.route.params.id}/todos`);
        const todos = await res.json();
        return {
            todos
        };
    },
}
</script>

<style scope>
.todo {
    border: 2px solid #eee;
    margin-bottom: 10px;
    padding: 5px;
}

.todo--completed {
    text-decoration: line-through;
}
</style>