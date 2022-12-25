<template>
    <div class="flex justify-center mt-24">
        <div class=" rounded shadow-md bg-white w-96 border-2 border-blue-500">
            <div class="border-b-2 border-blue-500 p-3">
                <h3 class="uppercase text-3xl text-blue-500 font-bold text-center">Register</h3>
            </div>
           <form @submit.prevent="register">
            <div class="p-3">
             <div class="mb-2">
                <label for="name">name <span class="text-red-500">*</span></label>
                <div>
                    <input type="text" v-model="form.name" class="px-2 py-1 rounded w-full border-2 border-gray-400">
                </div>
             </div>
             <div class="mb-2">
                <label for="email">Email <span class="text-red-500">*</span></label>
                <div>
                    <input type="email" v-model="form.email" class="px-2 py-1 rounded w-full border-2 border-gray-400">
                </div>
             </div>
             <div class="mb-2">
                <label for="password">Password <span class="text-red-500">*</span></label>
                <div>
                    <input type="password" v-model="form.password" class="px-2 py-1 rounded w-full border-2 border-gray-400">
                </div>
             </div>
             <div class="mb-2">
                <label for="password_confirmation">Confirm Password <span class="text-red-500">*</span></label>
                <div>
                    <input type="password" v-model="form.password_confirmation" class="px-2 py-1 rounded w-full border-2 border-gray-400">
                </div>
             </div>
             <p class="text-sm">Already registered? please <router-link class="text-blue-600 font-semibold text-sm" to="/">Login</router-link></p>
             <div>
                <button type="submit" class="bg-blue-500 text-white font-semibold text-sm w-full rounded  py-2 mt-2">Submit</button>
             </div>
            </div>
           </form>
        </div>
    </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";
import axios from "axios";
  
  const form = ref({
    name: null,
    email: null,
    password: null,
    password_confirmation: null
  })
  async function register() {
    await axios.get('http://localhost:8000/sanctum/csrf-cookie') 
    const res = await axios.post('http://localhost:8000/register', form.value)
    const user = await axios.get('http://localhost:8000/api/user')
  }
</script>

<style>

</style>