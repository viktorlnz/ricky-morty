<template>
  <q-page class="row items-center justify-evenly">
    <div class="text-h5">Personagens</div>
    <q-scroll-area class="scroll-area row">
      <character-component
        class="q-ma-md"
        v-for="(character, i) in characters"
        :key="i"
      />
    </q-scroll-area>
  </q-page>
</template>

<script setup lang="ts">
import CharacterComponent from 'src/components/character/CharacterComponent.vue';
import { ref } from 'vue';

const characters = ref([1, 2, 3, 4, 5, 6, 7, 89, 9, 4, 48, 8, 8, 8]);
</script>

<style lang="scss" scoped>
.scroll-area {
  width: 95%;
  min-width: 300px;
  height: calc(100vh - 200px);
}
</style>
