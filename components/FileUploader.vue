<template>
<div>
  <input type="file"
  multiple 
  @change="onFileSelected"
  ref="fileInput"/>
  <v-btn color="info" large flat
   @click="$refs.fileInput.click()">Upload Photos &nbsp; <v-icon>cloud_upload</v-icon>
  </v-btn>
  <v-card>
        <v-container grid-list-sm fluid>
          <v-layout row wrap>
            <v-flex
              v-for="n in 9"
              :key="n"
              xs4
              d-flex
            >
              <v-card flat tile class="d-flex">
                <v-img
                  :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
                  :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
                  aspect-ratio="1"
                  class="grey lighten-2"
                >
                  <v-layout
                    slot="placeholder"
                    fill-height
                    align-center
                    justify-center
                    ma-0
                  >
                    <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                  </v-layout>
                </v-img>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card>
      <v-btn @click="onUpload()">Upload</v-btn>
</div>
</template>

<script>
export default {
  data() {
    return {
      selectedFile: null,
    }
  },

  methods: {
    onFileSelected(event) {
      this.selectedFile = event.target.files
    },

    testUpload() {
      console.log('running')
      let token = 'ya29.c.ElpKBo5zuk3_6ufAy8JdnnNMD-1z25yl_zh1Ds-nPAiq8wImSpFytnoU4KkX1A-aKfISgFrNKBOUQ98gZrDxBgB9TVBx9sjCznuRJ-GBImLwbNW9EjjT6NZU29Y'
      let config = {
            headers: {'Authorization': "bearer " + token}
          };
      
      let body =  {
          "payload": {
          "image": {
          "imageBytes": "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"
          },
        }
      }
      
      endpoint = 'https://automl.googleapis.com/v1beta1/projects/skin-cancer-cal-hacks/locations/us-central1/models/ICN1091417111883437786:predict'
      axios.post(endpoint, body, config).then(res => {
        console.log(res)
      })
    },

    onUpload() {
      const fd = new FormData()
      fd.append('image', this.selectedFile, this.selectedFile.name)
      axios.post('api endpoint', fd, {
        onUploadProgress: uploadEvent => {
          console.log('Upload Progress: ' + Math.round((uploadEvent.loaded / uploadEvent.total) * 100))
        }
      }).then(
        res => {
          console.log('posted.')
        }
      )
    },

    mounted() {
      this.testUpload()
    }
  }
}
</script>

<style>

</style>
