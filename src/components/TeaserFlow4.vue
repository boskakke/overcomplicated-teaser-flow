<template>
  <div class="main-flow" :class="{ 'main-flow--inverted': inverted }">
    <div class="main-flow__main" >
      <Teaser :teaser="teasers[0]" class="t-main" />
    </div>
    <div class="main-flow__side main-flow__side-3 ">
      <Teaser :teaser="teasers[1]" />
      <Teaser :teaser="teasers[2]" />
      <Teaser :teaser="teasers[3]" />
    </div>
  </div>
</template>

<script setup>
import Teaser from "./Teaser.vue";
import { inject } from "@vue/runtime-core";

defineProps({
  teasers: {
    type: Array,
    required: true,
  },
});
let inverted = inject("inverted");
let teasers = inject("teasers");
</script>