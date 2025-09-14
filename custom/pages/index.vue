<template>
  <section class="page">
    <div class="mx-auto max-w-6xl grid grid-cols-6 gap-3">
      <CatalogProductGrid identifier="action-dvd" />
    </div>
  </section>
</template>

<script setup lang="ts">
useHead({
  title: 'Media Store by JMSE - My-Media.world',
  meta: [
    {name:'keywords',content: 'gummersbach,bergneustadt,my,media,world,my-media.world,my-media,my Media,filme,serien,kinofilme'},
    {
      name: "description",
      content:
        "My Media World, ist meine Welt der Medien gefüttert von TMDB mit Film Daten soll es erstmal zeigen was mit PocketStore.io möglich ist by JMSE.",
    },
  ],
});
</script>