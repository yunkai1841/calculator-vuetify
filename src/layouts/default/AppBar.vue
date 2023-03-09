<template>
  <v-app-bar flat>
    <v-app-bar-title>
      <v-icon icon="mdi-calculator-variant" />

      Simple Calculator
    </v-app-bar-title>

    <!-- dark theme switch -->
    <template v-slot:append>
      <v-switch
        v-model="darkTheme"
        @update:model-value="changeTheme"
        :prepend-icon="darkTheme ? 'mdi-weather-night' : 'mdi-weather-sunny'"
        hide-details
        inset
        class="mr-auto"
      />
    </template>
  </v-app-bar>
</template>

<script setup>
import { ref } from 'vue'
import { useTheme } from 'vuetify'

const darkTheme = ref(false)
const theme = useTheme()

const changeTheme = () => {
  theme.global.name.value = darkTheme.value ? 'dark' : 'light'
}
</script>
