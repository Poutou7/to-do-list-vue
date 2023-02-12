<template>
  <div class="header-task">
    <h1 class="logo">Todo</h1>
    <div class="date">
      <div>
        <span class="today">Today</span>
        <span class="day">{{ new Date().toDateString() }}</span>
      </div>
      <img src="../assets/calendar.png" alt="date" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'HeaderComp',
}
</script>

<style scoped>
.header-task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 15px;
  border-bottom: 1px solid #fbdfc5;
}

.header-task .logo {
  margin: 0;
  font-size: 2.5rem;
}

.header-task .date {
  display: flex;
  align-items: flex-start;
  gap: 10px;
}

.header-task .date .today {
  display: block;
  text-align: right;
  font-size: 21px;
  font-weight: bold;
}

.header-task .date .day {
  font-size: 13px;
  color: #777;
}
</style>