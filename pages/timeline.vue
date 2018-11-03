<template>
  <v-layout align-center justify-center>
    <v-flex xs12>      
      <v-card height="500px" light>
        <v-card-title class="blue-grey white--text">
          <span class="title">Timeline</span>
        </v-card-title>
        <v-card-text class="py-0">
          <v-timeline dense>
            <v-timeline-item
              v-for="story in stories"
              :key="story.title"
            >
              <v-card>
                <v-card-title>
                  <span class="title blue--text text--darken-2">{{story.title}}</span>
                </v-card-title>

                <v-card-text>
                  <p>{{story.date}}</p>
                </v-card-text>
              </v-card>
            </v-timeline-item>
          </v-timeline>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      stories: [
        {
          title: 'Nacimiento',
          center: [-40970, 4789238],
          zoom: 16,
          date: 'Diciembre 1993'
        },
        {
          title: 'Estudios',
          center: [-39000, 4789238],
          zoom: 14,
          date: 'Diciembre 1993'
        },
        {
          title: 'Universidad',
          center: [-38000, 4789238],
          zoom: 12,
          date: 'Diciembre 1993'
        },
      ]
    }
  }
}
</script>

<style>

</style>
