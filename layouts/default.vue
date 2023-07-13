<script lang="ts" setup>
import {useAuthStore} from '../stores/useAuthStore'
const auth = useAuthStore();


async function handleLogout(){
    await auth.logout()
}
</script>

<template>
    <div> 
        <GlobalHeader/>
        <UserStatus/>
        <pre v-if="auth.isLoggedIn">Hello, <b>{{ auth.user.name }}!</b></pre>
        <button v-if="auth.isLoggedIn" @click="handleLogout">Logout</button>
        <slot/>
    </div>
</template>