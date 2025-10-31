<template>
  <div class="col-span-6 md:col-span-2 py-3">
    <div v-if="product && product.cover" class="card shadow-xl bg-white">
      <figure>
        <a :href="'/' + locale + '/product/' + product.slug + '.html'">
          <img v-if="product.cover"
               :src="
                  url +
                  '/api/files/' +
                  product.collectionId +
                  '/' +
                  product.id +
                  '/' +
                  product.cover
                "
               alt="Shoes"
          />
        </a>
      </figure>
      <p class="text-sm font-bold text-center block py-2 px-2">
        Media by <a :href="'https://www.themoviedb.org/movie/'+product.tmdb" class="text-blue-500" target="_blank">themoviedb.org</a>
      </p>
      <div class="card-body">
        <h2 class="card-title text-ellipsis line-clamp-1">{{ product.name }}</h2>
        <p class="text-ellipsis line-clamp-2">{{ product.description }}</p>
        <div class="card-actions join gap-0 justify-end">
          <a
              v-if="product.price"
              :href="'/' + locale + '/product/' + product.slug + '.html'"
              class="btn btn-primary join-item"
          >
            {{ product.price.toFixed(2) }} €
          </a>
          <ProductAddToCart :stock="stock.quantity ?? 0" :item="product"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import {usePocketBase, usePocketBaseUrl} from "~/util/pocketbase";
import {useLocalStorage} from "@vueuse/core";

const pb = usePocketBase();
const url = usePocketBaseUrl();

const i18n = useI18n();
const locale = i18n.locale;
const stock = ref({});

const props = defineProps({
  identifier: {type: String, requiered: true},
});

const product = useLocalStorage("product-" + props.identifier + "", {}, {});
const date = useLocalStorage(
    "product-" + props.identifier + "-date",
    new Date().toLocaleDateString("de"),
    {}
);

function isEmpty(obj) {
  for (const prop in obj) {
    if (Object.hasOwn(obj, prop)) {
      return false;
    }
  }

  return true;
}

onMounted(async () => {
  if (
      product.value === null ||
      date.value != new Date().toLocaleDateString("de") ||
      isEmpty(product.value)
  ) {
    product.value = await pb
        .collection("products")
        .getFirstListItem('slug="' + props.identifier + '"');

    stock.value = await pb
        .collection("product_stocks")
        .getFirstListItem('product="' + product.value.id + '"');
    console.log(stock ?? 0);
  }
});
</script>