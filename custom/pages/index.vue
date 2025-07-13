<template>
  <section class="page">
    <div class="mx-auto max-w-6xl grid grid-cols-6 gap-3">
      <CatalogProductGrid identifier="action-dvd" />
    </div>
  </section>
</template>

<script setup lang="ts">
const { t } = useI18n();

useHead({
  title: 'Media Store by JMSE - My-Media.world',
  meta: [
    {
      name: "description",
      content:
        "My Media World, ist meine Welt der Medien gefüttert von TMDB mit Film Daten soll es erstmal zeigen was mit PocketStore.io möglich ist by JMSE.",
    },
  ],
});
</script>