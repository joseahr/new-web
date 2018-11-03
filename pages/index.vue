<template>
  <v-layout align-center justify-center>

    <v-flex xs12 sm8 md6>
      <v-card
        color="grey lighten-4"
        width="100%"
        hover
      >
        <v-img
          class="reverse-linear-gradient"
          :aspect-ratio="16/9"
          src="/hero.jpg"
        >
          <!-- <v-layout row wrap class="navigation-container">
            <v-toolbar dense style="background: rgba(0,0,0,0.5)">
              <v-btn
                :icon="$vuetify.breakpoint.xsOnly"
                :outline="$vuetify.breakpoint.smAndUp"
                :flat="$vuetify.breakpoint.xsOnly"
                to="/"
                disabled
                :nuxt="true"
                color="blue lighten-4">
                <v-icon>mdi-arrow-left</v-icon>
              </v-btn>
              <v-spacer></v-spacer>
              <v-toolbar-title class="mx-0">Inicio</v-toolbar-title>
              <v-spacer></v-spacer>
              <v-btn
                :icon="$vuetify.breakpoint.xsOnly"
                :outline="$vuetify.breakpoint.smAndUp"
                :flat="$vuetify.breakpoint.xsOnly"
                to="/about"
                :nuxt="true"
                color="blue lighten-4">
                <v-icon>mdi-arrow-right</v-icon>
              </v-btn>
            </v-toolbar>
          </v-layout> -->
        </v-img>
        <v-card-text
          class="pt-5"
          style="position: relative;"
        >
          <v-btn
            absolute
            fab
            large
            right
            top
            :ripple="false"
          >
            <v-avatar size="72px">
              <img src="/joseahr.jpg" alt="">
            </v-avatar>
          </v-btn>

          <h2 class="font-weight-dark orange--text text-xs-center">JOSE HERMOSILLA RODRIGO</h2>

          <!--<v-expansion-panel
            v-model="panel"
            expand
            light
            class="mt-2"
          >
            <v-expansion-panel-content
              v-for="(item, i) in items"
              :key="i"
            >
              <div slot="header" class="blue--text">{{item.header}}</div>
              <v-card>
                <v-card-text class="grey lighten-3" v-html="item.description"></v-card-text>
              </v-card>
            </v-expansion-panel-content>
          </v-expansion-panel>-->

        </v-card-text>

        <v-card-actions>
          <v-btn
            large
            icon
            light
            v-for="rrss in social"
            :key="rrss.icon"
            :href="rrss.href"
            target="_blank"
            outline
            :color="rrss.color"
            class="mx-auto">
            <v-icon :color="rrss.color">mdi-{{rrss.icon}}</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>

</template>

<script>
import '@mdi/font/css/materialdesignicons.css';
export default {
  data() {
    return {
      panel: [true, false, false],
      items: [
        {
          header: 'Sobre mí',
          description: `
          <p>Me presento, mi nombre es <b>Jose</b> y soy un apasionado de la tecnología, experto en <b>Sistemas de Información Geográfica</b> (SIG) y <b>Web Mapping.</b></p>
          <a style="font-weight: bold;" class="orange--text">¿QUIERES SABER MÁS?</a>
          `,
        },
      ],
      social: [
        {
          icon: 'github-circle',
          href: 'https://github.com/joseahr',
          color: 'black',
        },
        {
          icon: 'facebook',
          href: 'https://www.facebook.com/jose.hermosillarodrigo',
          color: 'blue darken-4',
        },
        {
          icon: 'stack-overflow',
          href: 'https://stackoverflow.com/users/3866134/jose-hermosilla-rodrigo?tab=profile',
          color: 'orange',
        },
        {
          icon: 'instagram',
          href: 'https://www.instagram.com/josehermosillarodrigo/',
          color: 'brown',
        },
        {
          icon: 'linkedin',
          href: 'https://www.linkedin.com/in/jose-%C3%A1ngel-hermosilla-rodrigo-70a590147/',
          color: 'blue'
        },
      ],
    };
  },
}
</script>

<style>
.reverse-linear-gradient {
  background: linear-gradient(to left,rgba(255, 187, 0, 0.8), rgba(0, 187, 255, 0.5)) !important;
}

.v-image__image--cover {
  mix-blend-mode: darken;
}

.navigation-container {
  position: absolute;
  top: 0px; left: 0px; right: 0px;
  z-index: 1;
}
</style>
