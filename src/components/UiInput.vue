<template>
  <input
    class="input"
    type="text"
    :placeholder="props.placeholder"
    @input="getInputValue"
    :value="props.id"
  />
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  placeholder: {
    type: String,
  },
  id: {
    type: String,
  },
  title: {
    type: String,
    required: false,
  },
});

const emit = defineEmits(["getInputValue"]);
const getInputValue = (event) => {
  emit("getInputValue", event.target.value);
};
</script>

<style lang="scss" scoped>
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>
