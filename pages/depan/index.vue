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

    <br />
    <template>
      <div class="text-center">
        <v-btn class="ma-2" outlined color="indigo" :to="'/depan/create'"
          >Tambah</v-btn
        >
      </div>
    </template>

    <template>
      <v-row>
        <v-col cols="12" sm="10" offset-sm="1">
          <v-card>
            <v-container fluid>
              <v-row>
                <ListItem
                  v-for="resep in reseps"
                  :id="String(resep.id)"
                  :key="String(resep.id)"
                  :judul="resep.judul"
                  :by="resep.by"
                  :keterangan="resep.keterangan"
                  :resep="resep.resep"
                  :gambar="resep.gambar"
                  @muat-ulang="getData"
                ></ListItem>
              </v-row>
            </v-container>
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
import Axios from 'axios'
import Carousel from '~/components/carousel'
import ListItem from '~/components/list-item'

export default {
  components: { ListItem, Carousel },
  data() {
    return {
      reseps: [],
      isError: false,
      isEmpty: false,
      isLoading: false
    }
  },
  mounted() {
    this.getData()
  },
  methods: {
    async getData() {
      this.isLoading = true

      try {
        const res = await Axios.get('http://localhost:3001/resep')
        this.reseps = res.data

        if (this.reseps.length === 0) {
          this.isEmpty = true
        }
      } catch (err) {
        console.error(err)

        this.isError = true
      }

      this.isLoading = false
    }
  }
}
</script>
