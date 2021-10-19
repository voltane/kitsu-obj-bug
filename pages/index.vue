<template>
  <Tutorial/>
</template>

<script lang="ts">
import {defineComponent} from "@vue/composition-api";
import Kitsu from "kitsu";

export default defineComponent({
  setup() {
    const kitsu = new Kitsu()
    // In SSR throws [object Object] is not an Option Object
    kitsu.fetch('/abstract-products', {
      params: {
        include: 'abstract-product-image-sets,abstract-product-prices',
        fields: {
          'abstract-products': 'name,age',
          'abstract-product-image-sets': 'id,imageSets',
          'abstract-product-prices': 'price',
        },
      },
    }).then(
        (response: any) => {
            console.log('abstract product response ', response)
        }
    )
  }
})
</script>
