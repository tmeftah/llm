<template>
  <q-layout view="hHh lpR fFf">
    <q-header dark bordered class="bg-white text-grey-8">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title
          class="text-bold text-weight-bolder text-h3"
          style="color: #507295"
        >
          Aora.
        </q-toolbar-title>
        <!-- Orion Inova -->
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered :width="220">
      <q-list>
        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "Dashboard",
    caption: "overview",
    icon: "line_axis",
    link: "/",
  },
  {
    title: "Ask a question",
    caption: "chat with docs",
    icon: "chat_bubble_outline",
    link: "/query",
  },
  {
    title: "Alle Dokumente",
    caption: "chat with docs",
    icon: "folder_open",
    link: "documents",
  },
];

const leftDrawerOpen = ref(false);
const miniState = ref(true);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
