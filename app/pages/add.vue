<script setup>
const config = useRuntimeConfig()
const baseUrl = config.public.base_url
const router = useRouter()
let showDetails = {
  id: Math.random(),
  title: '',
  desc: '',
  type: '',
  release_year: '',
  run_time: '',
  genres: '',
  img_url: '',
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
}

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
    alert('Show Added Successfully')
    refreshNuxtData('showDeatils')
    router.push('/discover')
  } else {
    alert(data.error.value)
  }
}
</script>

<template>
  <div class="container">
    <h3 class="text-center my-2">Add New Shows</h3>
    <FormShows
      :show-details="showDetails"
      @handle-submit="handleSubmit"
    ></FormShows>
  </div>
</template>
