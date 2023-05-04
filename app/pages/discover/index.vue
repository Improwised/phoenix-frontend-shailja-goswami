<script setup>
const config = useRuntimeConfig()
const baseUrl = config.public.base_url
const route = useRoute()
let _page = route.query._page
const url = `${baseUrl}/title?_page=${_page}&_limit=2`
const { data: showsData, pending } = await useFetch(url)
const searchString = ref('')
let shows = {
  data: showsData,
  isPending: pending,
}
async function clickNext() {
  _page = parseInt(_page) + 1
  window.location.href = `/discover?_page=${_page}`
}
async function clickPrev() {
  _page = parseInt(_page) - 1
  window.location.href = `/discover?_page=${_page}`
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
    <div class="d-flex justify-content-center mt-4">
      <nav>
        {{}}
        <ul class="pagination">
          <li :class="['page-item', _page <= 1 ? 'disabled' : '']">
            <a
              class="page-link theme-pagination cursor-pointer"
              tabindex="-1"
              @click="clickPrev()"
              >Previous</a
            >
          </li>
          <li :class="['page-item', showsData.length == 0 ? 'disabled' : '']">
            <button class="page-link theme-pagination" @click="clickNext()">
              Next
            </button>
          </li>
        </ul>
      </nav>
    </div>
  </section>
</template>
<style>
.theme-pagination {
  background-color: rgba(47, 128, 237, 0.1);
  color: aliceblue;
  position: relative;
  display: block;
  text-decoration: none;
  border: 1px solid rgba(47, 128, 237, 0.1);
  transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
    border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
.theme-pagination:hover {
  background-color: rgba(47, 128, 237, 0.1) !important;
  color: aliceblue !important;
}
.theme-pagination:focus {
  background-color: rgba(47, 128, 237, 0.1) !important;
  color: aliceblue !important;
}
.disabled > .page-link,
.page-link.disabled {
  background-color: rgba(47, 128, 237, 0.1);
  border-color: rgba(47, 128, 237, 0.1);
}
.active > .page-link,
.page-link.active {
  background-color: #151f30;
  border-color: #151f30;
}
</style>
