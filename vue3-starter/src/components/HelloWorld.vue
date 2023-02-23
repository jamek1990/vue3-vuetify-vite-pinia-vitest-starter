<script setup lang="ts">
import { ref } from "vue";
import { Form } from "vee-validate";
import * as Yup from "yup";
import TextInput from "./TextInput.vue";

defineProps<{ msg: string }>();

const count = ref(0);

function onSubmit(values) {
  alert(JSON.stringify(values, null, 2));
}

const schema = Yup.object().shape({
  name: Yup.string().required(),
});
</script>

<template>
  <Form @submit="onSubmit" :validation-schema="schema">
    <TextInput
      name="name"
      label="Full Name"
      placeholder="Your Name"
      v-model="count"
    />
  </Form>

  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
