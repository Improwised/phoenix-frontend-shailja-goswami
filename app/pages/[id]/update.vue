<script setup>
const config = useRuntimeConfig()
const baseUrl = config.public.base_url
const router = useRouter()
const route = useRoute()
const id = route.params.id
const noDataFound = ref(false)
let showDetails = {
  id: '',
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
      person_id: '',
      title_id: '',
      name: '',
      character: '',
      role: '',
      img_url: '',
    },
  ],
}
const { data } = await useFetch(`${baseUrl}/title/${id}`)
if (data.value === null) {
  noDataFound.value = true
} else {
  noDataFound.value = false
  showDetails = data
}
async function apiCall(addDetails) {
  const data = await useFetch(`${baseUrl}/title/${id}`, {
    headers: { 'Content-type': 'application/json' },
    method: 'PUT',
    body: addDetails.id ? JSON.stringify(addDetails) : '',
  })
  return data
}
async function handleSubmit(addDetails) {
  const data = await apiCall(addDetails)
  if (data.error.value == null) {
    alert('Show updated Successfully')
    refreshNuxtData('showDeatils')
    router.push('/discover')
  } else {
    alert(data.error.value)
  }
}
</script>

<template>
  <div class="container">
    <h3 class="text-center mt-4 mb-3">Update Show</h3>
    <FormShows
      v-if="!noDataFound"
      :show-details="showDetails"
      @handle-submit="handleSubmit"
    ></FormShows>
  </div>
</template>
