<template>
  <div>
    <v-card>
      <v-img
            :src=source
          ></v-img>
      <v-card-title primary-title>
        <div>
          <h3 class="headline mb-0">{{ title }}</h3>
        </div>
      </v-card-title>

      <v-card-actions>
        <v-btn flat color="orange">Share</v-btn>
        <v-btn flat color="orange">Explore</v-btn>
      </v-card-actions>
  </v-card>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    source: String,
  }
}
</script>

<style>

</style>
