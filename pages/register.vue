<template>
    <div>
        <form @submit.prevent="handleRegister">
            <label>
                Name
                <input type="text" v-model="form.name">
            </label>
            <label>
                Email
                <input type="email" v-model="form.email">
            </label>
            <label>
                Password
                <input type="Password" v-model="form.password">
            </label>
            <label>
                Password
                <input type="Password" v-model="form.password_confirmation">
            </label>
            <button>Register</button>
        </form>
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
const form = ref({
  name: '',
  email: '',
  password: '',
  password_confirmation: '' 
});
import { useAuthStore } from '../stores/useAuthStore';
const auth = useAuthStore();

async function handleRegister() {
  const { error } = await auth.register(form.value);
  console.log(error);
}
</script>
