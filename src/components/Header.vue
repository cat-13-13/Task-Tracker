<template>
    <header>
        <h1>{{title}}</h1>
        <CommonButton @toggle-add-task="$emit('toggle-add-task')" 
        :text="showAddTask ? 'Close' : 'Add Task'" 
        :color="showAddTask ? 'red' : 'blue'" />

    </header>
</template>

<script>
  import CommonButton from './Button.vue'

  export default {
    name: 'HeaderTitle',
    props: {
      title: String,
      showAddTask: Boolean
    },
    components: {
      CommonButton,
    }
  }
</script>

<style  scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>