<script setup lang="ts">
import { toRef } from "vue";
import { useField } from "vee-validate";

const props = defineProps({
  value: {
    type: String,
    default: "",
  },
  name: {
    type: String,
    required: true,
  },
  label: {
    type: String,
    required: true,
  },
  placeholder: {
    type: String,
    default: "",
  },
});

const name = toRef(props, "name");

const { value: inputValue, errorMessage } = useField(name, undefined, {
  initialValue: props.value,
});
</script>

<template>
  <v-text-field
    :name="name"
    v-model="inputValue"
    clearable
    hide-details="auto"
    :label="label"
    :placeholder="placeholder"
    :error="errorMessage == ''"
    :error-messages="errorMessage"
  ></v-text-field>
</template>

<style scoped>
</style>
