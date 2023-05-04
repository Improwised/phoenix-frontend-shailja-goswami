<script setup>
const route = useRoute()
const queryParam = route.params.type
const config = useRuntimeConfig()
const base_url = config.public.base_url
const url = `${base_url}/title?type=${queryParam}`
const { data: showsData, pending } = await useFetch(url)

let show = {
  data: showsData,
  isPending: pending,
}
</script>

<template>
  <div class="container">
    <h2 class="mt-4">
      {{ queryParam == 'SHOW' ? 'Explore All Tv Shows' : 'Explore All Movies' }}
    </h2>
    <Shows :shows-data="show"></Shows>
  </div>
</template>
