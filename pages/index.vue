<template>
  <v-layout
    column
    justify-center
    align-center>
      <v-card>
        <v-card-title class="headline">
          Concerned about your skin? You should be.
        </v-card-title>
        <v-card-text>
          We developed a machine learning algorithm to analyze and detect possibly cancerous
          skin samples using pictures that you securely upload.
        </v-card-text>
        <v-card-actions>
          <v-btn>Find out</v-btn>
        </v-card-actions>
      </v-card>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  }
}
</script>
