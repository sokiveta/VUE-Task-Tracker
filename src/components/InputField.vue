<template>
  <div class="form-control">
    <label :for="name">{{ label }}</label>
    <input
      type="text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      :id="name"
      :name="name"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
export default {
  name: 'InputField',
  data() {
    return {};
  },
  props: {
    modelValue: {
      type: String,
      required: true,
    },
    name: String,
    label: String,
    placeholder: String,
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
