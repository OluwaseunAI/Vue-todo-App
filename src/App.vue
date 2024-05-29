<script>
  import Navbar from "./components/Navbar.vue";
  import Tasks from "./components/Tasks.vue";
  import Form from "./components/Form.vue";

  export default {
    name: "App",
    components: {
      Navbar,
      Form,
      Tasks,
    },
    data() {
      return {
        tasks: [
          {
            text: "Meeting with friends dspr",
            date: "jun 5th 2024",
            reminder: true,
          },
          {
            text: "Study Vue js. Implement a blog",
            date: "jun 6th 2024",
            reminder: true,
          },
          {
            text: "Study NodeJs",
            date: "july 20th 2024",
            reminder: false,
          },
        ],
        showForm: false,
      };
    },
    methods: {
      addTasks(tasks){
        this.tasks = [tasks, ...this.tasks];
        // this.text = title
      },
      deleteTask(index){
        this.tasks.splice(index, 1);
      },
      toggleForm(showForm){
        this.showForm = !this.showForm
    },
  },
  }
</script>

<template>
  <Navbar @toggle-form="toggleForm" />
  <Form v-if="showForm" @add-task="addTasks"/>
  <Tasks :tasks="tasks" @delete-task="deleteTask" />

</template>

<style></style>
