<template>
  <section class="page">
    <div class="mx-auto max-w-6xl grid grid-cols-6 gap-3">
      <ins class="adsbygoogle"
           style="display:block"
           data-ad-client="1250525441896834"
           data-ad-slot="YOUR_SLOT_ID"
           data-ad-format="auto"></ins>
      <CatalogProductGrid identifier="action-dvd" />
    </div>
  </section>
</template>

<script setup lang="ts">
useHead({
  title: 'Media Store by JMSE - My-Media.world',
  meta: [
    {name:'keywords',content: 'jmse,media store,store,movies,gummersbach,bergneustadt,my,media,world,my-media.world,my-media,my media,filme,serien,kinofilme'},
    {
      name: "description",
      content:
        "My Media World, ist meine Welt der Medien gefüttert von TMDB mit Film Daten soll es erstmal zeigen was mit PocketStore.io möglich ist by JMSE.",
    },
  ],
  script: [{
    async: true,
    src: 'https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-1250525441896834'
  }]
});

onMounted(()=>{
  nextTick(()=>{
    console.log('tick: ',window.adsbygoogle);
    if (window.adsbygoogle) {
      window.adsbygoogle.push({});
    }
  })
});
</script>