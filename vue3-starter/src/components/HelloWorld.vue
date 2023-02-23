<script setup lang="ts">
import { ref } from "vue";
import { Form } from "vee-validate";
import * as Yup from "yup";
import TextInput from "./TextInput.vue";

defineProps<{ msg: string }>();

const count = ref(123);

function onSubmit(values) {
  alert(JSON.stringify(values, null, 2));
}

const schema = Yup.object().shape({
  name: Yup.string().required(),
});
</script>

<template>
  <v-layout>
      <v-app-bar title="Application bar"></v-app-bar>

      <v-navigation-drawer>
        <v-list>
          <v-list-item title="Navigation drawer"></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-main style="min-height: 300px;"> <br><br>
      <v-row> <v-col cols="12" style=" padding:50px;">
      
      <v-alert
    type="success"
    title="Alert title"
    text="Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, ratione debitis quis est labore voluptatibus! Eaque cupiditate minima, at placeat totam, magni doloremque veniam neque porro libero rerum unde voluptatem!"
  ></v-alert>
    <br>
  <v-text-field label="Label" hide-details="auto"></v-text-field>
    <br>
  <Form @submit="onSubmit" :validation-schema="schema">

    <TextInput
      name="name"
      label="Full Name"
      placeholder="Your Name"
      v-model="count"
      :readonly=true
    />

  <br>

    <TextInput
      name="name"
      label="Full Name"
      placeholder="Your Name"
      v-model="count"
      :readonly=false
    />
  </Form>

  <h1>{{ msg }}</h1>
     <v-btn
        color="error"
      >
        Large Button
      </v-btn>

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
</v-col>
      </v-row>
  </v-main>
    </v-layout>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
