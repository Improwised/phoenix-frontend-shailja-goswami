<script setup>
const props = defineProps(['showDeatils'])
const title = ref(props.showDeatils.title)
const description = ref(props.showDeatils.description)
const type = ref(props.showDeatils.type)
const releaseYear = ref(props.showDeatils.releaseYear)
const runTime = ref(props.showDeatils.runTime)
const genres = ref(props.showDeatils.genres)
const imgUrl = ref(props.showDeatils.imgUrl)
const productionCountry = ref(props.showDeatils.productionCountr)
const role = ref(props.showDeatils.credits.role)
const name = ref(props.showDeatils.credits.name)
const img_url = ref(props.showDeatils.credits.img_url)
const character = ref(props.showDeatils.credits.character)
let details = {
  title: title.value,
  description: description.value,
  type: type.value,
  release_year: releaseYear.value,
  run_time: runTime.value,
  genres: genres.value,
  img_url: imgUrl.value,
  production_country: productionCountry.value,
  credits: [
    {
      title_id: title.value,
      name: name.value,
      character: character.value,
      role: role.value,
      img_url: img_url.value,
    },
  ],
}
watchEffect(() => {
  details = {
    title: title.value,
    description: description.value,
    type: type.value,
    release_year: releaseYear.value,
    run_time: runTime.value,
    genres: genres.value,
    img_url: imgUrl.value,
    production_country: productionCountry.value,
    credits: [
      {
        title_id: title.value,
        name: name.value,
        character: character.value,
        role: role.value,
        img_url: img_url.value,
      },
    ],
  }
})
const emit = defineEmits(['handleSubmit'])

function submitForm() {
  console.log(details)
  if (details.title !== '' && details.type !== '') {
    emit('handleSubmit', details)
  } else {
    alert('Please enter all required details')
  }
}
</script>

<template>
  <div>
    <div class="card card-show-brief">
      <div class="card-body">
        <form class="row g-3 needs-validation">
          <div class="col-md-6">
            <label for="title" class="form-label">Title</label>
            <input
              id="title"
              v-model="title"
              type="text"
              class="form-control search-input"
              placeholder="Movie name"
              required
            />
          </div>
          <div class="invalid-feedback">Please choose a username.</div>
          <div class="col-md-6">
            <label for="type" class="form-label">Type</label>
            <select
              id="type"
              v-model="type"
              class="form-select search-input"
              aria-label="Choose"
              required
            >
              <option selected>Choose...</option>
              <option value="tvShow">Tv Show</option>
              <option value="movie">Movie</option>
            </select>
          </div>
          <div class="invalid-feedback">Please choose a username.</div>
          <div class="col-12">
            <label for="description" class="form-label">Description</label>
            <input
              id="description"
              v-model="description"
              type="text"
              class="form-control search-input"
              placeholder="Description"
            />
          </div>
          <div class="col-md-4">
            <label for="releaseYear" class="form-label">Release Year</label>
            <input
              id="releaseYear"
              v-model="releaseYear"
              type="number"
              pattern="[1-9]{1}[0-9]{3}"
              class="form-control search-input"
              placeholder="Show's release year"
            />
          </div>
          <div class="col-4">
            <label for="runTime" class="form-label">Run Time</label>
            <input
              id="runTime"
              v-model="runTime"
              type="number"
              class="form-control search-input"
              placeholder="Show run time"
            />
          </div>
          <div class="col-md-4">
            <label for="genres" class="form-label">genres</label>
            <select
              id="genres"
              v-model="genres"
              class="form-select search-input"
              aria-label="genres"
            >
              <option value="" selected>Choose...</option>
              <option value="drama">Drama</option>
              <option value="comedy">Comedy</option>
              <option value="action">Action</option>
              <option value="thiller">Thiller</option>
              <option value="horror">Horror</option>
            </select>
          </div>

          <div class="col-md-6">
            <label for="imgUrl" class="form-label"
              >Show's Poster Image Url</label
            >
            <input
              id="imgUrl"
              v-model="imgUrl"
              type="text"
              class="form-control search-input"
              placeholder="URl starting with http:// "
            />
          </div>
          <div class="col-md-6">
            <label for="productionCountry" class="form-label"
              >Production Country</label
            >
            <select
              id="productionCountry"
              v-model="productionCountry"
              class="form-select search-input"
              aria-label="productionCountry"
            >
              <option value="" selected>Choose...</option>
              <option value="UK">UK</option>
              <option value="US">US</option>
              <option value="India">India</option>
              <option value="China">China</option>
              <option value="Japan">Japan</option>
            </select>
          </div>
          <h4 class="pt-2">Add Show's Cast</h4>
          <div class="col-md-6">
            <label for="name" class="form-label">Name</label>
            <input
              id="name"
              v-model="name"
              type="text"
              class="form-control search-input"
              placeholder="Person's name"
            />
          </div>
          <div class="col-md-6">
            <label for="character" class="form-label">character Name</label>
            <input
              id="character"
              v-model="character"
              type="text"
              class="form-control search-input"
              placeholder="Character name"
            />
          </div>
          <div class="col-md-6">
            <label for="role" class="form-label">Role</label>
            <input
              id="role"
              v-model="role"
              type="text"
              class="form-control search-input"
              placeholder="Role"
            />
          </div>
          <div class="col-md-6">
            <label for="image" class="form-label">Image</label>
            <input
              id="image"
              v-model="img_url"
              type="text"
              class="form-control search-input"
              placeholder="Image URL"
            />
          </div>

          <div class="col-12 text-center mb-2 mt-4">
            <button
              type="submit"
              class="btn btn-primary"
              @click.prevent="submitForm(details)"
            >
              Add Show
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
