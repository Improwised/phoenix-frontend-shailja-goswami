<script setup>
const config = useRuntimeConfig()
const baseUrl = config.public.base_url
let showDeatils = reactive({
  id: Math.random(),
  title: '',
  description: '',
  type: '',
  release_year: '',
  run_time: '',
  genres: '',
  imgUrl: '',
  production_country: '',
  credits: [
    {
      person_id: Math.random(),
      title_id: '',
      name: '',
      character: '',
      role: '',
      img_url: '',
    },
  ],
})

async function apiCall(addDetails) {
  const data = await useFetch(`${baseUrl}/title`, {
    headers: { 'Content-type': 'application/json' },
    method: 'POST',
    body: JSON.stringify(addDetails),
  })
  return data
}
async function handleSubmit(addDetails) {
  const data = await apiCall(addDetails)
  if (data.error.value == null) {
    alert(data.value.title + ' ' + 'Show Added Successfully')
    refreshNuxtData('showDeatils')
  } else {
    alert(data.error.value)
  }
}
</script>

<template>
  <div class="container">
    <h3 class="text-center my-2">Add New Shows</h3>
    <FormShows
      ref="addUpdateForm"
      :show-deatils="showDeatils"
      @handle-submit="handleSubmit"
    ></FormShows>
  </div>
</template>
