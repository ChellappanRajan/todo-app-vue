<template>
  <form class="w-full max-w-sm" v-on:submit="onSubmit">
  <div class="flex items-center border-b border-b-2 border-teal-500 py-2">
    <input v-model="title" class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="Add Todo" aria-label="Full name">
    <button
    v-on:click="onAdd"
     class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="button">
      Add Todo
    </button>
  </div>
</form>

  
</template>

<script>
export default {
  name: "AddTodo",
  //I have tried to use arrow function. It seem vue will loose current vue context if we use arrow function.
  //So using object function will solve this issue.
  //In Vue we can use event modifier like :stop to prevent default. more are available
  methods: {
    onAdd() {
     const newTodo = {
       title: this.title,
       id: new Date().toISOString(),
       completed: true
     }
     this.$emit('add-todo', newTodo);
     this.title = '';
    },
    onSubmit(e) {
      e.prventDefault();
    }
  },
  data: function() {
      return {
          title: ''
      };
  }
};
</script>


<style  scoped>
.form-control {
}
.form-control label {
}
.form-control input {
  padding: 0.5rem 1rem;
}
</style>