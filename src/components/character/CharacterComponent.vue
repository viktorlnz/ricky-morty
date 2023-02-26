<template>
  <q-card class="card">
    <q-img class="card__image" :src="props.character.image" />

    <div class="text-caption text-wrap">{{ props.character.name }}</div>
  </q-card>
</template>

<script lang="ts" setup>
import ICharacter from 'src/interfaces/ICharacter';

const props = defineProps<{ character: ICharacter }>();
</script>

<style lang="scss">
.card {
  max-width: 250px;

  &__image {
    width: 250px;
  }
  .text-caption {
    white-space: normal !important;
  }
}
</style>
