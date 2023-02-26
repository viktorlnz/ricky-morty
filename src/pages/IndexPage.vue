<template>
  <q-page class="row items-center justify-evenly">
    <div class="text-h5">Personagens</div>
    <q-scroll-area class="scroll-area">
      <div class="row">
        <character-component
          class="q-ma-md"
          v-for="(character, i) in characters"
          :key="i"
          :character="character"
        />
      </div>
    </q-scroll-area>
    <div class="q-px-xl div-btns">
      <q-btn
        label="Anterior"
        @click="(ev) => changePage(beforeUrl)"
        color="green-6"
      />
      <q-btn
        label="Próximo"
        @click="(ev) => changePage(afterUrl)"
        color="green-6"
      />
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { api } from 'src/boot/axios';
import CharacterComponent from 'src/components/character/CharacterComponent.vue';
import { ref, onMounted } from 'vue';
import ICharacter from '../interfaces/ICharacter';

const characters = ref<ICharacter[]>([]);
const beforeUrl = ref(null);
const afterUrl = ref(null);

onMounted(async () => {
  searchCharacters();
});

async function searchCharacters(url: string | null = null) {
  const { data } = await api.get(url ?? '/character');

  const searchedCharacters = <ICharacter[]>[];

  for (const result of data.results) {
    const character: ICharacter = {
      id: result.id,
      name: result.name,
      image: result.image,
      episodes: result.episode,
    };

    searchedCharacters.push(character);
  }

  characters.value = searchedCharacters;
  console.log(data);
  console.log(characters.value);

  beforeUrl.value = data.info.prev;
  afterUrl.value = data.info.next;
}

function changePage(value: string | null) {
  searchCharacters(value);
}
</script>

<style lang="scss" scoped>
.scroll-area {
  width: 100%;
  min-width: 300px;
  height: calc(100vh - 200px);
}

.q-page .div-btns {
  max-width: 500px;
  width: 100%;
  background-color: red;
  display: flex;
}
</style>
