<script lang="ts" setup>
import { usePocketBase } from "~/util/pocketbase";
import { defineProps ,onUpdated,onMounted} from "vue";
import {Head} from "@vueuse/head";
import {useHead} from "../../../storefront/.nuxt/imports";

const props = defineProps({
    product: { type: Object, required: true },
});

const pb = usePocketBase();
const loadSeo = async () => {
  if (props.product) {
        const productSeo = await pb
            .collection("product_seo")
            .getFirstListItem('product="' + props.product.id + '"');
        if(productSeo.product && props.product.name) {
          useHead({
            title: props.product.name + " - Produkt Ansicht",
            meta: [
              {
                name: "description",
                content: productSeo.desc,
              },
            ],
          });
        }
    }
};

onUpdated(() => {
    loadSeo();
});

onMounted(async () => {
    loadSeo();
});
</script>
