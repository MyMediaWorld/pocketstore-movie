<template>
    <section class="page min-h-screen" data-theme="light">
        <header>
            <Header />
        </header>
        <main class="mx-auto max-w-6xl min-h-screen px-3 2xl:px-0">
            <Messages />
            <Breadcrumb />
            <CookieBanner />
            <BackToTop />
            <slot />
        </main>
        <footer>
            <Footer />
        </footer>
    </section>
</template>
<script setup lang="ts">
import "../main.css";
import Footer from "~/components/Footer.vue";
import Header from "~/components/Header.vue";
</script>

<style scoped>
.page {
  --s: 80px; /* control the size*/
  --c1: #542437;
  --c2: #c02942;
  
  --_g: 
    #0000 calc(-650%/13) calc(50%/13),var(--c1) 0 calc(100%/13),
    #0000 0 calc(150%/13),var(--c1) 0 calc(200%/13),
    #0000 0 calc(250%/13),var(--c1) 0 calc(300%/13);
  --_g0: repeating-linear-gradient( 45deg,var(--_g));
  --_g1: repeating-linear-gradient(-45deg,var(--_g));
  background:
    var(--_g0),var(--_g0) var(--s) var(--s),
    var(--_g1),var(--_g1) var(--s) var(--s) var(--c2);
  background-size: calc(2*var(--s)) calc(2*var(--s));
}
</style>

