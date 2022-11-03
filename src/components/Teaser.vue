<template>
  <div class="teaser" :class="teaser.class">
    <figure class="teaser__figure">
      <img :src="getImage()" alt="" />
    </figure>
    <div class="teaser__body">
      <h2 class="teaser__title">{{ teaser.title }}</h2>
    </div>

    <select name="className" v-model="teaser.class" class="teaserControls">
      <option value="t-default" selected>Image right</option>
      <option value="t-hide-image">Hide image</option>
      <option value="t-vertical">Vertical</option>
      <option value="t-large">Large</option>
    </select>
  </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";

const props = defineProps({
  teaser: {
    type: Object,
    required: true,
  },
});

// const className = ref("t-default");
const getImage = () => {
  
  const id = 238 + props.teaser.id
  const path = `https://picsum.photos/id/${id}/1000/667`
  return path
}
</script>

<style scoped>
.teaser {
  position: relative;
}
img {
  max-width: 100%;
}
.teaserControls {
  position: absolute;
  top: 0;
}
</style>