<template>
  <ul class="tasks-created" v-if="allTasks.length > 0">
    <div v-for="(ts, index) in allTasks" :key="index">
      <li @click="finishTask(ts, index)">
        <input type="checkbox" />
        <label class="task-name">{{ ts }}</label>
      </li>
      <i class="fa-regular fa-trash-can" @click="deleteTask(index)"></i>
    </div>
  </ul>
  <button :style="{ opacity: allTasks.length > 1 ? '1' : '0' }" @click="deleteAll">Delete All Tasks</button>
  <ul class="end-task" v-if="endTasks.length > 0">
    <li v-for="(endTask, i) in endTasks" :key="i">
      <input type="checkbox" id="end-task" />
      <label for="end-task">{{ endTask }}</label>
    </li>
  </ul>
</template>
<script>
export default {
  name: 'NewTask',
  props: ['tasks'],
  data() {
    return {
      allTasks: this.tasks,
      endTasks: [],
    }
  },
  methods: {
    deleteTask(index) {
      this.allTasks.splice(index, 1);
    },
    finishTask(v, index) {
      this.endTasks.push(v);
      this.deleteTask(index);
    },
    deleteAll() {
      this.allTasks = [];
    }
  },
}
</script>

<style scoped>
.all-tasks .tasks-created,
.all-tasks .end-task {
  margin: 0;
  list-style: none;
  padding: 20px 0 0;
}

.all-tasks .tasks-created div {
  display: flex;
  justify-content: space-between;
}

.all-tasks .tasks-created i {
  font-size: 18px;
  margin-right: 60px;
  cursor: pointer;
  opacity: 0.5;
  transition: 0.4s;
}

.all-tasks .tasks-created i:hover {
  opacity: 1;
}

.all-tasks .end-task {
  border-top: 1px solid #fbdfc5;
  margin-top: 20px;
}


.all-tasks .tasks-created li,
.all-tasks .end-task li {
  position: relative;
  padding-left: 35px;

}

.all-tasks .tasks-created li:not(:last-child),
.all-tasks .end-task li:not(:last-child) {
  margin-bottom: 23px;
}

.all-tasks .tasks-created li::before {
  border-color: #4d53f0;
  cursor: pointer;
}

.all-tasks .end-task li::before {
  border-color: #a7a7a7;
  background-color: #f1f1f1;
  cursor: not-allowed;
}

.all-tasks .tasks-created li::before,
.all-tasks .end-task li::before {
  content: '';
  position: absolute;
  width: 23px;
  height: 23px;
  border-width: 2px;
  border-style: solid;
  left: 0;
  top: -3px;
}

.all-tasks .end-task li::after {
  content: '\f00c';
  font-family: 'Font Awesome 6 Free';
  font-weight: bold;
  position: absolute;
  left: 6px;
  top: 1px;
  color: #a7a7a7;
  font-size: 17px;
  cursor: not-allowed;
}

.all-tasks .tasks-created input[type="checkbox"],
.all-tasks .end-task input[type="checkbox"] {
  appearance: none;
}

.all-tasks .tasks-created label {
  font-size: 18px;
  cursor: pointer;
}

.all-tasks .end-task label {
  color: #888;
  text-decoration: line-through;
  font-size: 18px;
  cursor: not-allowed;
}

.all-tasks button {
  display: block;
  background-color: #d26702;
  color: #fff;
  border: none;
  font-size: 17px;
  cursor: pointer;
  padding: 10px;
  margin: 0 auto;
  font-size: 13px;
  font-weight: bold;
  opacity: 0;
  transition: 0.3s;
}
</style>