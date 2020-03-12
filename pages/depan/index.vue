<template>
  <div>
    <v-card class="overflow-hidden">
      <v-app-bar
        absolute
        color="#fcb69f"
        dark
        shrink-on-scroll
        src="https://picsum.photos/1920/1080?random"
        scroll-target="#scrolling-techniques-2"
      >
        <template v-slot:img="{ props }">
          <v-img
            v-bind="props"
            gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
          ></v-img>
        </template>

        <v-app-bar-nav-icon></v-app-bar-nav-icon>

        <v-toolbar-title>Cookin</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>
    </v-card>
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <Carousel></Carousel>
    <template>
      <v-row>
        <v-col cols="12" sm="10" offset-sm="1">
          <v-card>
            <v-container>
              <v-row>
                <v-col
                  v-for="n in 9"
                  :key="n"
                  class="d-flex child-flex"
                  cols="4"
                >
                  <v-card max-width="500" class="mx-auto">
                    <v-list-item>
                      <v-list-item-avatar color="grey"></v-list-item-avatar>
                      <v-list-item-content>
                        <v-list-item-title class="headline"
                          >Our Changing Planet</v-list-item-title
                        >
                        <v-list-item-subtitle
                          >by Kurt Wagner</v-list-item-subtitle
                        >
                      </v-list-item-content>
                    </v-list-item>

                    <v-img
                      src="https://cdn.vuetifyjs.com/images/cards/mountain.jpg"
                      height="194"
                    ></v-img>

                    <v-card-text
                      >Visit ten places on our planet that are undergoing the
                      biggest changes today.</v-card-text
                    >

                    <v-card-actions>
                      <v-btn text color="deep-purple accent-4">Read</v-btn>
                      <v-btn text color="deep-purple accent-4">Bookmark</v-btn>
                      <v-spacer></v-spacer>
                      <v-btn icon>
                        <v-icon>mdi-heart</v-icon>
                      </v-btn>
                      <v-btn icon>
                        <v-icon>mdi-share-variant</v-icon>
                      </v-btn>
                    </v-card-actions>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
            <template>
              <div class="text-center">
                <v-pagination
                  v-model="page"
                  :length="4"
                  prev-icon="mdi-menu-left"
                  next-icon="mdi-menu-right"
                ></v-pagination>
              </div>
            </template>
          </v-card>
        </v-col>
      </v-row>
    </template>

    <template>
      <v-row>
        <v-col cols="12" sm="10" offset-sm="1">
          <v-card>
            <v-container fluid>
              <v-row>
                <v-col
                  v-for="n in 12"
                  :key="n"
                  class="d-flex child-flex"
                  cols="2"
                >
                  <v-card flat tile class="d-flex">
                    <v-img
                      :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
                      :lazy-src="
                        `https://picsum.photos/10/6?image=${n * 5 + 10}`
                      "
                      aspect-ratio="1"
                      class="grey lighten-2"
                    >
                      <template v-slot:placeholder>
                        <v-row
                          class="fill-height ma-0"
                          align="center"
                          justify="center"
                        >
                          <v-progress-circular
                            indeterminate
                            color="grey lighten-5"
                          ></v-progress-circular>
                        </v-row>
                      </template>
                    </v-img>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </div>
</template>
<script>
import Carousel from '~/components/carousel'

export default {
  components: {
    Carousel
  },
  data() {
    return {
      page: 1
    }
  }
}
</script>
