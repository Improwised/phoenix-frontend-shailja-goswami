<script setup>
const props = defineProps(['showsData'])
const config = useRuntimeConfig()
const base_url = config.public.base_url
const shows = ref(props.showsData.data)
const isPending = ref(props.showsData.isPending)

async function deleteShow(id, show) {
  if (confirm('Are you sure you wanted to remove ' + show + ' this show')) {
    const deleted = await useFetch(`${base_url}/title/${id}`, {
      method: 'DELETE',
    })
    window.location.href = '/discover'
  } else {
    return
  }
}
</script>

<template>
  <div>
    <div v-if="isPending" class="text-center mt-5">
      <div class="spinner-border text-info" role="status"></div>

      <div class="mt-3">Loading...</div>
    </div>
    <div v-else class="row">
      <div
        v-for="(show, index) in shows"
        :key="index"
        class="col-md-4 col-lg-3 col-sm-10 g-4"
      >
        <div class="card card-show-brief">
          <img
            :src="show.img_url"
            class="card-img-top img-show"
            :alt="show.title"
          />
          <div class="card-body">
            <h5 class="card-title text-truncate">{{ show.title }}</h5>
            <div class="card-text">
              <div class="show-desc text-gray mt-2">
                {{ show.desc }}
              </div>
              <div class="d-flex justify-content-between mt-3">
                <div class="text-truncate text-gray">
                  Played: {{ show.runtime }}
                </div>
                <div class="text-truncate text-gray">{{ show.type }}</div>
                <div class="text-truncate text-gray">
                  {{ show.release_year }}
                </div>
              </div>
              <div class="d-flex justify-content-between mt-3">
                <NuxtLink :to="`/${show.id}/update`"
                  ><img
                    src="~/assets/images/icons/edit.svg"
                    class="main__table-btn btn_edit"
                /></NuxtLink>
                <img
                  src="~/assets/images/icons/delete.svg"
                  class="main__table-btn btn_delete cursor-pointer"
                  data-bs-toggle="modal"
                  data-bs-target="#exampleModal"
                  @click="deleteShow(show.id, show.title)"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
