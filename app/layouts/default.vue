<script setup>
import twitter from '~/assets/images/icons/twitter.svg'
import instagram from '~/assets/images/icons/instagram.svg'
import facebook from '~/assets/images/icons/facebook.svg'
import voko from '~/assets/images/icons/vokodesign.svg'
import tictok from '~/assets/images/icons/tictok.svg'
</script>
<template>
  <div>
    <!-- Nav bar started -->
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

              <li class="nav-item px-2">
                <NuxtLink class="nav-link active" aria-current="page" to="/"
                  >Discover</NuxtLink
                >
              </li>
              <li class="nav-item px-2">
                <NuxtLink class="nav-link active" aria-current="page" to="/"
                  >Add Show</NuxtLink
                >
              </li>
            </ul>
          </form>
        </div>
      </div>
    </nav>
    <!-- Nav bar ended -->
    <div class="main-content">
      <slot></slot>
    </div>

    <!-- footer started-->
    <footer class="footer">
      <div class="container">
        <div class="row">
          <div class="col-md-6 col-lg-4 offset-md-3 offset-lg-4 pt-5">
            <div class="d-flex justify-content-between pt-5">
              <div class="pt-5">
                <img :src="twitter" />
              </div>
              <div class="pt-5">
                <img :src="facebook" />
              </div>
              <div class="pt-5">
                <img :src="instagram" />
              </div>
              <div class="pt-5">
                <img :src="voko" />
              </div>
              <div class="pt-5">
                <img :src="tictok" />
              </div>
            </div>
            <div class="d-flex justify-content-around pt-5">
              <div>
                <NuxtLink to="/" class="white-text-link">Home</NuxtLink>
              </div>
              <div>
                <NuxtLink to="/" class="white-text-link">Discover</NuxtLink>
              </div>
              <div>
                <NuxtLink to="/" class="white-text-link">Update</NuxtLink>
              </div>
              <div>
                <NuxtLink to="/" class="white-text-link">Movie</NuxtLink>
              </div>
              <div>
                <NuxtLink to="/" class="white-text-link">Tv show</NuxtLink>
              </div>
            </div>
          </div>
          <div class="footer__content">
            <div class="col-md-6 col-12 offset-md-3 pt-5">
              <div
                class="d-flex flex-md-row flex-column justify-content-md-between justify-content-center"
              >
                <div class="mt-4 mt-md-0 text-center">
                  © FlixTV.Show, 2023. Created by Shailja
                </div>
                <div class="mt-4 mt-md-0 text-center">
                  <NuxtLink to="/" class="white-text-link"
                    >Privacy ploicy</NuxtLink
                  >
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
    <!-- footer ended -->
  </div>
</template>
