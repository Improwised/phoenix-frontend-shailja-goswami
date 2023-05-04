<script setup>
const config = useRuntimeConfig()
const baseUrl = config.public.base_url
const { data: showsData, pending } = await useFetch(`${baseUrl}/title`)
const searchString = ref('')
const searchedShow = computed(() => {
  return showsData.value.filter((shows) => {
    return (
      shows.title.toLowerCase().indexOf(searchString.value.toLowerCase()) != -1
    )
  })
})
let shows = {
  data: searchedShow,
  isPending: pending,
}
</script>

<template>
  <section class="container pt-md-5">
    <div
      class="d-flex justify-content-between card-show-brief p-3 align-items-center"
    >
      <div class="col-3">
        <input
          v-model="searchString"
          class="form-control search-input"
          placeholder="Search for Movies and Tv show"
        />
      </div>
      <div>
        <NuxtLink to="/add" class="text-decoration-none white-text-link"
          >Add Show
        </NuxtLink>
      </div>
    </div>
    <div class="col-12">
      <Shows :shows-data="shows"></Shows>
    </div>
  </section>
</template>
