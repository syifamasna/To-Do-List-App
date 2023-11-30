<template>
  <main>
    <h1>To Do List</h1>
    <p>Organize your life and complete tasks more reliably</p>

    <div class="create-new">
      <input 
        type="text" 
        v-model="newTask" 
        placeholder="what do we do today?" 
        @keypress.enter="addTask" />
      <button @click="addTask">ADD</button>
    </div>

    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data (){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
