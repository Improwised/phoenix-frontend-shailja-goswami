<script setup>
const config = useRuntimeConfig()
const baseUrl = config.public.base_url
console.log(baseUrl)
const { data: showsData, pending } = await useLazyFetch(`${baseUrl}/title`)
const searchString = ref('')
let shows = {
  data: showsData,
  isPending: pending,
}
</script>

<template>
  <section class="container pt-md-5">
    <div class="col-4 offset-8">
      <input
        v-model="searchString"
        class="form-control"
        placeholder="Search for Movies and Tv show"
      />
    </div>
    <div class="col-12">
      <Shows :shows-data="shows"></Shows>
    </div>
  </section>
</template>
