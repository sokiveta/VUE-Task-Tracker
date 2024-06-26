<script setup>
import { ref } from 'vue';
import InputField from './InputField';
let message = ref('');
let day = ref('');
</script>
<template>
  <form @submit="onSubmit" class="add-form">
    <InputField
      name="message"
      label="Task"
      placeholder="Add Task"
      v-model="message"
    />
    <InputField
      name="day"
      label="Day & Time"
      placeholder="Add Day & Time"
      v-model="day"
    />
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <div>Task: {{ message }}</div>
    <div>Day: {{ day }}</div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      message: '',
      day: '',
      reminder: false,
    };
  },
  components: {
    InputField,
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!message.value) {
        alert('Please add a task');
        return;
      }
      if (!day.value) {
        alert('Please add the date and time');
        return;
      }
      const newTask = {
        // id: Math.floor(Math.random() * 100000),
        message: message.value,
        day: day.value,
        reminder: this.reminder,
      };

      this.$emit('add-task', newTask);
      message.value = '';
      day.value = '';
      this.reminder = false;
      this.$emit('toggle-add-task');
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
