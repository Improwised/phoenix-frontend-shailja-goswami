<script setup>
/*Define Pinia store*/
/*import { useUsersStore } from '~/store/users'
const UsersStore = useUsersStore()
console.log(UsersStore);*/
definePageMeta({
  layout: 'default',
})
useHead({
  bodyAttrs: {
    class: 'bg-navy',
  },
})
</script>
<template>
  <div class="text-center homepage vh-100">Welcome to nuxt3</div>
  <div class="text-center homepage vh-100">Welcome to nuxt3</div>
  <div class="text-center homepage vh-100">Welcome to nuxt3</div>
</template>
<style scoped>
.homepage {
  margin-top: 400px;
  font-size: 30px;
}
</style>
