<script setup>
import { reactive, ref } from "@vue/reactivity";
import TeaserFlow3 from "./components/TeaserFlow3.vue";
import TeaserFlow4 from "./components/TeaserFlow4.vue";
import TeaserFlow5 from "./components/TeaserFlow5.vue";
import TeaserFlow6 from "./components/TeaserFlow6.vue";

import { provide } from "@vue/runtime-core";

const counter = ref(3);
const inverted = ref(false);
provide("inverted", inverted);

const teasers = reactive([
  {
    title: "Forskere: Gråt hår kan faktisk genvinde sin farve",
    class: "skakke",
    id: 1,
  },
  {
    title: "Forskere er et skridt tættere på en kur mod skaldede isser",
    class: "skakke",
    id: 2,
  },
  {
    title: "Videnskabens største kontroverser: Italiensk læge vil transplantere et hoved",
    class: "skakke",
    id: 3,
  },
  {
    title: "Ægtepar bag covid-vaccine: Så hurtigt kan vi have en kræft-vaccine klar",
    class: "skakke",
    id: 4,
  },
  {
    title: "Så meget strøm og vand sparer øko-programmet",
    class: "skakke",
    id: 5,
  },
  {
    title: "Kæmpe undersøgelse: Så mange skridt skal du gå om dagen for at leve længere",
    class: "skakke",
    id: 6,
  },
]);
</script>

<template>
  <main>
    <div class="container">
      <div class="controls">
        <div class="radio">
          <div v-for="index in 4" :key="index">
            <label>
              <input
                :checked="index == 1"
                type="radio"
                :name="counter"
                v-model="counter"
                :value="index + 2"
                :id="`counter-${index}`"
              />
              {{ index + 2 }}
            </label>
          </div>
        </div>
        <div>
          <label for="inverted-design">
            <input
              type="checkbox"
              v-model="inverted"
              value=""
              id="inverted-design"
            />
            Inverted
          </label>
        </div>
      </div>

      <TeaserFlow3 :teasers="teasers" v-if="counter == 3" />

      <TeaserFlow4 :teasers="teasers" v-if="counter == 4" />

      <TeaserFlow5 :teasers="teasers" v-if="counter == 5" />

      <TeaserFlow6 :teasers="teasers" v-if="counter == 6" />
    </div>
  </main>
</template>

<style scoped lang="scss">
.controls {
  border-radius: 5px;
  background-image: linear-gradient(to bottom, lighten(#333, 4%), #333);
  border: 1px solid #444;
  z-index: 2;
  width: 100%;
  margin: 4rem 0;
  display: flex;
  align-items: center;
  padding: 1rem;
  gap: 1rem;
  position: sticky;
  top: 1rem;
}
.radio {
  display: flex;
  gap: 1rem;
}
label {
  cursor: pointer;
}
</style>


