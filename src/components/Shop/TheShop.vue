<script setup lang="ts">
import { Ref, provide, ref } from "vue";

import { SECTIONS, typeSections } from "./sections";
import { srcPngHelper } from "../common/utils";

import Title from "./TheTitle.vue";
import Assortment from "./TheAssortment.vue";

const selected = ref<typeSections>(SECTIONS.ALL);

provide<Ref<typeSections>>("selectedPlatforms", selected);
</script>

<template>
  <div class="shop">
    <Title
      :selected-section="selected"
      @select-section="(s) => (selected = s)"
    />
    <div class="shop__body">
      <Assortment />
    </div>
    <img :src="srcPngHelper('castle')" alt="" />
  </div>
</template>

<style scoped>
.shop {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 0 10px;
  background-color: #6b8cff;
}

.shop__body {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
  align-content: flex-start;
  padding: 10px;
  gap: 50px 80px;
}

.shop > img {
  margin: 0 -10px;
}
</style>
