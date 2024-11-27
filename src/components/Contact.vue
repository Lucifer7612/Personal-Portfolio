<template>
  <div class="">
    <div class="text-center">
      <button @click="toContact" class="p-3">Contact</button>
    </div>
    <div class="flex flex-col justify-center items-center" v-if="isVisual">
      <label for=""
        >Enter your Name:
        <input
          type="text"
          name="name"
          placeholder="enter your full name"
          id="name"
          v-model="name"
          class=""
      /></label>
      <br />
      <br />
      <label for=""
        >Enter your Email:
        <input
          type="email"
          name="email"
          id="email"
          v-model="email"
          placeholder="yahooo@gmail.com"
          class=""
      /></label>
      <br />
      <br />
      <label for="" class="flex justify-center items-center"
        >How can I help??:
        <textarea
          type="text"
          name="help"
          rows="4"
          cols="50"
          v-model="help"
          class=""
        ></textarea></label
      ><br />
      <br />
      <button @click="addData" class="p-3">Submit</button>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import { axiosApi } from "./lib/axios";

const isVisual = ref(false);
const name = ref("");
const email = ref("");
const help = ref("");

const toContact = () => {
  isVisual.value = !isVisual.value;
};
//---------------------------------------------------Validation

//---------------------------------------------------ApicallPost
const addData = async () => {
  // console.log("Abcdefgh");
  try {
    const response = await axiosApi.post("/api/users/", {
      name: name.value,
      email: email.value,
      help: help.value,
    });
    console.log(response.data);
  } catch (error) {
    console.error("Error sending data:", error);
  }
};
</script>
