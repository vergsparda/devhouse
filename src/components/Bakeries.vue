<template>
    <SplitCarousel class="bakeries-slider" 
    :height="60"
    :interval="999999999"
    :autoplay="false"
    :item-width="170">
      <SplitCarouselItem
        class="list-item"
        v-for="image in images"
        :key="image.index"
        >
          <img class="list-image" :src="image"/>
      </SplitCarouselItem>
    </SplitCarousel>
</template>

<script>
import { SplitCarousel, SplitCarouselItem } from "vue-split-carousel";

export default {
  name: "Bakeries",
  props: {
    images: {
      type: Array,
    },
  },
  components: {
    SplitCarousel,
    SplitCarouselItem,
  },

  data: function () {
    return {
    };
  },
};
</script>

<style scoped>
.bakeries-slider {
  margin-top: 30px;
}

.list-image {
  width: 20vw;
  max-width: 100%;
}
</style>
