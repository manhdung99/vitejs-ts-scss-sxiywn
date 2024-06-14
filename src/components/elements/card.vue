<template>
  <div class="card">
    <div class="card-image">
      <img :src="imageSrc" alt="Card image" />
    </div>
    <div class="card-content">
      <p class="card-text">{{ description }}</p>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { computed, nextTick, ref } from "vue";
const props = defineProps<{
  imageSrc: string;
  description: string;
}>();
</script>
<style scoped>
.card {
  background: white;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
.card-image {
  width: 100%;
  padding-top: 66.66%; /* 3:2 aspect ratio */
  position: relative;
}
.card-image img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.card-text {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  font-weight: 700;
  margin: 0;
  padding: 4px 4px;
}
</style>
