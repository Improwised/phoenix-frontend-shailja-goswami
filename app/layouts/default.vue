<template>
  <nav class="navbar nav-navy navbar-expand-lg">
    <div class="container">
      <NuxtLink to="/"
        ><img
          src="http://flixtv.volkovdesign.com/main/img/logo.svg"
          class="img-fluid"
      /></NuxtLink>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div id="navbarSupportedContent" class="collapse navbar-collapse">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0"></ul>
        <form class="d-flex">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item px-2">
              <NuxtLink class="nav-link active" aria-current="page" to="/"
                >Home</NuxtLink
              >
            </li>
          </ul>
        </form>
      </div>
    </div>
  </nav>
</template>
