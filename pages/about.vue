<template>
  <v-layout align-center justify-center>
    <v-flex xs12 sm8 md6>
      <v-card
        color="grey lighten-4"
        width="100%"
        hover
        v-if="story >= 0"
      >
        <v-responsive :aspect-ratio="16/9">
          <vl-map
            ref="map"
            class="map reverse-linear-gradient"
            style="pointer-events: none;"
            load-tiles-while-animating
            @mounted="onMapMounted">
            <vl-view
              ref="view"
              :center.sync="center"
              :zoom.sync="zoom"></vl-view>
            <vl-layer-tile ref="baselayer" id="bing" :visible="true" :opacity="0.6">
              <vl-source-bing-maps imagery-set="CanvasGray" :api-key="apiKey"></vl-source-bing-maps>
            </vl-layer-tile>
          </vl-map>
        </v-responsive>


        <v-card-text>
          <v-timeline dense>
            <v-slide-x-reverse-transition
              group
              hide-on-leave
            >
              <v-timeline-item
                v-for="item in currentStories"
                :key="item.title"
                color="blue"
                small
                fill-dot
                icon="mdi-calendar"
              >
                <v-alert
                  :value="true"
                  color="blue"
                  icon="mdi-calendar"
                  @click="next"
                >
                  {{item.title}}
                </v-alert>
              </v-timeline-item>
            </v-slide-x-reverse-transition>
          </v-timeline>
        </v-card-text>

      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import '@mdi/font/css/materialdesignicons.css';
export default {
  data() {
    return {
      apiKey: 'AkeFKQTvXCZD5Dt-4_WHQ2XGQmOtITolLgL1XAtg4f_8KnruD_c6WdUXHpB7jigK',
      center: [-40970, 4789238],
      zoom: 15,
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
      ],
      story: 0,
      currentStories: [],
    };
  },

  mounted() {
    this.createCurrentStories();
  },

  methods: {
    async onMapMounted() {
      const map = this.$refs.map.$map;
      const view = this.$refs.view.$view;
      // const baselayerRef = this.$refs.baselayer;

      map.getControls().forEach(map.removeControl.bind(map));
      map.getInteractions().forEach(map.removeInteraction.bind(map));
    },

    next() {
      const value = this.story == this.stories.length - 1 ? 0 : 1;
      this.story += value;
      if(value) {
        this.currentStories.unshift(this.stories[this.story]);
      }
    },

    previous() {
      const value = this.story == 0 ? 0 : 1;
      this.story -= value;

      if(value) {
        this.currentStories.shift();
      }
    },

    createCurrentStories() {
      this.currentStories.push(this.stories[0]);
    },
  },

  watch: {
    story() {
      const view = this.$refs.view.$view;
      const { center, zoom } = this.stories[this.story];

      view.cancelAnimations();
      view.animate({ center, duration: 500 }, { zoom, duration: 250 });
    },
  },
};
</script>

<style>
.map {
  width: 100%;
  height: 100%;
}

.reverse-linear-gradient {
  background: linear-gradient(to left,rgba(255, 187, 0, 0.8), rgba(0, 187, 255, 0.5)) !important;
}
</style>
