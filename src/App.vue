<template>
  <div class="header">
    <div class="header-content">
      <div class="logo-wrapper">
        <img :src="logo" alt="" srcset="" />
      </div>
      <div class="action-wrapper">
        <button class="simple-button">Indie Game</button>
        <button class="simple-button">Entry Game</button>
        <button class="simple-button">Community</button>
      </div>
    </div>
  </div>
  <div :style="`font-size:${fontSize}px`" class="main-content">
    <div class="select-wrapper">
      <h2>Photo Cards</h2>
      <div>
        <span style="font-weight: 700"> Font-size: </span>
        <select name="fontSize" id="fontSize" v-model="fontSize">
          <option v-for="number in numberList" :value="number">
            {{ number }}
          </option>
        </select>
      </div>
    </div>
    <div class="list-image">
      <card
        v-for="number in numberList"
        :key="number"
        :image-src="number % 2 == 0 ? image1 : image2"
        description="Product name is quite long in some cases"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import logo from "./assets/images/logo.png";
import image1 from "./assets/images/image1.jpg";
import image2 from "./assets/images/image2.png";
import card from "./components/elements/card.vue";
import { computed, ref } from "vue";

const numberList = computed(() => {
  return Array.from({ length: 28 }, (_, i) => i + 1);
});
const fontSize = ref(13);
</script>
<style lang="scss">
body {
  margin: 0;
}
.header {
  background: #2ccd9b;
  padding: 0 4px;
  color: white;
  overflow: hidden;
  .header-content {
    display: flex;
    padding: 20px 0;
    justify-content: space-between;
    align-items: center;
    max-width: 1536px;
    width: 100%;
    margin: auto;
  }
  .action-wrapper {
    display: flex;
    column-gap: 10px;
    .simple-button {
      border: 1px solid #fff;
      background: transparent;
      color: white;
      padding: 8px 8px;
      border-radius: 4px;
      cursor: pointer;
    }
    :hover {
      font-weight: 700;
    }
  }
}
.main-content {
  max-width: 1536px;
  width: 100%;
  margin: auto;
  .list-image {
    margin: 0 4px;
    display: grid;
    grid-gap: 12px;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  }
  .select-wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 4px;
  }
}
// @media (min-width: 550px) {
//   .list-image {
//     grid-template-columns: repeat(2, 1fr);
//   }
// }

// @media (min-width: 750px) {
//   .list-image {
//     grid-template-columns: repeat(3, 1fr);
//   }
// }
@media (min-width: 1536px) {
  .list-image {
    grid-template-columns: repeat(6, 1fr) !important;
  }
}
</style>
