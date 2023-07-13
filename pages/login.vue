<template>
    <div>
        <form @submit.prevent="handleLogin">
            <label>
                Email
                <input type="email" v-model="form.email">
            </label>
            <label>
                Password
                <input type="Password" v-model="form.password">
            </label>
            <button>Login</button>
        </form>
    </div>
</template>

<script lang="ts" setup>
import {ref} from 'vue';

const form = ref({
    email : "test@example.com",
    password: "password"
});
import {useAuthStore} from '../stores/useAuthStore'
const auth = useAuthStore();
async function handleLogin(){
    const {error} = await auth.login(form.value)
    console.log(error)
};




</script>