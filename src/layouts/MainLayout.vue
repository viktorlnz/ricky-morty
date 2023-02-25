<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title> Ricky and Morty </q-toolbar-title>
        <SearchBar />
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer>
      <div class="text-body2">&copy; Todos os direitos reservados</div>
    </q-footer>
  </q-layout>
</template>

<script setup lang="ts">
import SearchBar from 'src/components/searchBar/SearchBar.vue';
</script>
