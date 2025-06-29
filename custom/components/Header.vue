<template>
  <div>
    <section class="mx-auto max-w-6xl flex justify-between">
      <section class="logo">
        <a href="/">
          <img src="/pocketstore-favicon.svg" class="h-16" />
        </a>
      </section>
      <nav class="navigation-bars md:hidden">
        <button v-if="!open" @click="open = !open">
          <FontAwesomeIcon :icon="faBars" size="2x" />
        </button>
        <button v-else @click="open = !open">
          <FontAwesomeIcon :icon="faTimes" size="2x" />
        </button>
      </nav>
      <nav class="content hidden md:block">
        <ul class="flex flex-col md:flex-row space-x-5 mt-5">
          <li>
            <a href="/" class="btn btn-sm btn-primary btn-block">Startseite</a>
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
    </section>
    <section v-if="open">
      <section class="grid grid-cols-6 gap-3">
        <div class="col-span-3">
          <a href="/" class="btn btn-block btn-primary">Startseite</a>
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