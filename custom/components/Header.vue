<template>
  <div>
    <section class="mx-auto max-w-6xl px-3 lg:px-0 py-3">
      <div class="bg-gray-400 flex justify-between">
        <section class="logo px-3 py-3">
          <a href="/" class="flex items-center">
            <img src="/pocketstore-favicon.svg" class="h-12" />
            <span class="ml-3 text-lg font-bold">
                My-Media.World
            </span>
          </a>
        </section>
        <nav class="navigation-bars md:hidden mt-5 mr-3">
          <button v-if="!open" @click="open = !open">
            <FontAwesomeIcon :icon="faBars" size="2x" />
          </button>
          <button v-else @click="open = !open">
            <FontAwesomeIcon :icon="faTimes" size="2x" />
          </button>
        </nav>
        <nav class="content hidden md:block">
          <ul class="flex flex-col md:flex-row space-x-5 mt-5 mr-3">
            <li>
              <a href="/" class="btn btn-sm btn-primary btn-block"
                >Startseite</a
              >
            </li>
            <li>
              <a href="/de/checkout" class="btn btn-sm btn-primary btn-block"
                >Checkout</a
              >
            </li>
            <li>
              <a href="/de/categories" class="btn btn-sm btn-primary btn-block"
                >Categories</a
              >
            </li>
            <li>
              <a
                href="/de/category/action-dvd.html"
                class="btn btn-sm btn-primary btn-block"
                >Category</a
              >
            </li>
            <li>
              <a
                href="/de/brand/test-123"
                class="btn btn-sm btn-primary btn-block"
                >Brand</a
              >
            </li>
          </ul>
        </nav>
      </div>
    </section>
    <section v-if="open">
      <section class="grid grid-cols-6 gap-3 bg-gray-400 px-3 py-3 mx-3 mb-3">
        <div class="col-span-3">
          <a href="/" class="btn btn-block btn-primary">Startseite</a>
        </div>
         <div class="col-span-3">
          <a href="/de/checkout" class="btn btn-block btn-primary">Kasse</a>
        </div>
        <div class="col-span-3">
          <a href="/de/brands/test-123" class="btn btn-block btn-primary">Brand</a>
        </div>
        <div class="col-span-3">
          <a href="/de/categories" class="btn btn-block btn-primary">Kategorien</a>
        </div>
        <div class="col-span-3">
          <a href="/de/category/action-dvd.html" class="btn btn-block btn-primary">Kategorie</a>
        </div>
        <div class="col-span-3">
          <a href="/de/wishlist" class="btn btn-block btn-primary">Wunschliste</a>
        </div>
      </section>
    </section>
  </div>
</template>

<script setup lang="ts">
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faBars, faTimes } from "@fortawesome/free-solid-svg-icons";
import { useLocalStorage } from "@vueuse/core";

const open = useLocalStorage("open-navigation-content", false, {});

onMounted(() => {
  open.value = false;
});
</script>