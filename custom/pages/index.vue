<template>
  <section class="page">
    <div class="mx-auto max-w-6xl grid grid-cols-6 gap-3">
      <CatalogProductGrid identifier="action-dvd" />
    </div>
  </section>
</template>

<script setup lang="ts">
import config from "./../pocketstore.json";
const { t } = useI18n();
useHead({
  title: t("general.title"),
  meta: [
    {
      name: "Media Store by JMSE - My-Media.world",
      content:
        "My Media World, ist meine Welt der Medien gefüttert von TMDB mit Film Daten soll es erstmal zeigen was mit PocketStore.io möglich ist by JMSE.",
    },
  ],
});
</script>