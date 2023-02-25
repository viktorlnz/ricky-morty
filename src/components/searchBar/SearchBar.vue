<template>
  <div class="div-search">
    <q-input
      outlined
      v-model="search"
      class="q-my-sm input-search"
      bg-color="white"
      label="Pesquisar um nome"
    >
      <template v-slot:append>
        <q-icon name="search" @click="test" />
      </template>
    </q-input>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const search = ref('');

const test = () => {
  console.log(search.value);
};
</script>

<style lang="scss" scoped>
.div-search {
  max-width: 250px;
  width: 35%;

  .input-search {
    font-size: 0.8rem;
  }
}
</style>
