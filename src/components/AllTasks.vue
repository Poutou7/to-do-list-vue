<template>
  <div class="all-tasks">
    <form>
      <input type="text" placeholder="Add a new task" v-model="task" />
      <button @click.prevent="addTask">
        <i class="fa-solid fa-plus"></i>
      </button>
    </form>
    <span v-if="error == 'error' && tasks" class="error">Please, Enter a new task</span>
    <NewTask :tasks="tasks" />
  </div>
</template>

<script>
import NewTask from './NewTask.vue'
export default {
  name: 'AllTasks',
  components: {
    NewTask
  },
  data() {
    return {
      tasks: [],
      task: '',
      error: '',
    }
  },
  methods: {
    addTask() {
      if (this.task == '') {
        this.error = 'error';
      } else {
        this.error = '';
        this.tasks.push(this.task);
        this.task = '';
      }
    }
  },
}
</script>

<style scoped>
.all-tasks {
  padding: 15px 0 0;
}

.all-tasks form {
  width: 100%;
  display: flex;
  gap: 10px;
}

.all-tasks form input {
  flex: 1;
  padding: 12px;
  border: 1px solid #ddd;
  background-color: #fcfbfc;
  color: #555;
}

.all-tasks form input::placeholder {
  color: #d0d0d0
}

.all-tasks form input:focus {
  outline: none;
}

.all-tasks button {
  background-color: #4d53f0;
  color: #fff;
  border: none;
  width: 45px;
  height: 45px;
  font-size: 17px;
  cursor: pointer;
}

.all-tasks .error {
  display: block;
  margin-top: 5px;
  font-size: 15px;
  color: #c42306;
}
</style>