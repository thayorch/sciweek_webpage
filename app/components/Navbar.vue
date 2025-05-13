<template>
  <div class="bg-transparent d-flex justify-end px-4">
    <div class="d-flex gap-3">
      <v-btn
        variant="plain"
        class="text-white"
        size="large"
        density="compact"
        icon="mdi-home"
        to="/"
      />
      <FullscreenBtn />
    </div>

    <v-menu >
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          variant="plain"
          class="text-white pt-1"
          size="large"
          density="compact"
          icon="mdi-menu"
        />
      </template>

      <v-list class="text-left pa-0 bg-transparent text-white">
        <v-list-subheader class="text-white font-weight-bold"
          >PAGES
        </v-list-subheader>

        <v-list-item to="/"> Dashbord </v-list-item>
        <v-list-item to="/quiz"> Quiz Game </v-list-item>
        <v-list-item to="/moss"> Moss Game </v-list-item>
        <v-list-item to="/vial"> Vial Game </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>