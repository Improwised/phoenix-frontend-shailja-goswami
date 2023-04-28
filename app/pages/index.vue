<script setup>
/*Define Pinia store*/
/*import { useUsersStore } from '~/store/users'
const UsersStore = useUsersStore()
console.log(UsersStore);*/
definePageMeta({
  layout: 'default',
})
</script>
<template>
  <div class="text-center homepage">Welcome to nuxt3</div>
</template>
<style scoped>
.homepage {
  margin-top: 400px;
  font-size: 30px;
}
</style>
