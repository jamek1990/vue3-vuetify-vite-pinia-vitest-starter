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
  readonly: {
    type: Boolean,
    required: false,
    default: false,
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
    hide-details="auto"
    :label="label"
    :placeholder="placeholder"
    :error="errorMessage == ''"
    :error-messages="errorMessage"
    :readonly="readonly"
    variant="outlined"
    :class="{ readonly: readonly }"
    density="compact"
  ></v-text-field>
</template>

<style >

.readonly{
    background: #e9f3f7 none !important;
    
}


</style>
