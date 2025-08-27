<template>
  <template v-for="product in products" :key="product.id">
    <CatalogProductCard v-if="product.cover" :identifier="product.slug" />
  </template>
</template>

<script setup>
import { usePocketBase } from "~/util/pocketbase";
const pb = usePocketBase();

const { identifier } = defineProps({
    identifier: { type: String, required: true },
});

const category = ref({});
const products = ref([]);

onMounted(async () => {
    category.value = await pb
        .collection("categories")
        .getFirstListItem('slug="' + identifier + '"');
    products.value = (
        await pb.collection("products").getList(1, 12, {
            filter: 'category="' + category.value.id + '" && cover!=""',
            sort: '-created'
        })
    ).items;
});
</script>
