<template>
  <v-layout>
    <v-navigation-drawer v-model="drawer" color="primary" disable-resize-watcher>
      <v-list nav>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :active="i === 0"
          link
          :title="item.text"
        />
      </v-list>
    </v-navigation-drawer>

    <v-app-bar class="px-md-4">
      <template #prepend>
        <v-app-bar-nav-icon
          v-if="$vuetify.display.smAndDown"
          @click="drawer = !drawer"
        />
      </template>

   

      <template v-if="$vuetify.display.mdAndUp">
        <v-btn
          v-for="(item, i) in items"
          :key="i"
          :active="i === 0"
          class="me-2 text-none"
          slim
          v-bind="item"
        />
      </template>

      <v-spacer />

     
    </v-app-bar>

    <v-main height="200">
      <!--  -->
    </v-main>
  </v-layout>
</template>

<script setup>
  import { shallowRef } from 'vue'

  const drawer = shallowRef(false)

  const items = [
    {
      text: 'Dashboard',
    },
    {
      text: 'Users',
    },
    {
      text: 'Projects',
    },
    {
      text: 'Settings',
    },
    {
      text: 'Contact',
    },
  ]
</script>
