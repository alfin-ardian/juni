<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12" sm="10" offset-sm="1">
        <v-card class="mx-auto" max-width="344">
          <v-img :src="resep.gambar" height="200px"></v-img>

          <v-card-title>
            {{ judul }}
          </v-card-title>

          <v-card-subtitle>
            by :
            {{ by }}
          </v-card-subtitle>

          <v-card-actions>
            <v-btn :to="'/depan/' + id + '/edit'" color="purple" text>
              edit
            </v-btn>

            <v-btn @click="hapus" color="purple" text>
              hapus
            </v-btn>

            <v-spacer></v-spacer>

            <v-btn icon @click="show = !show">
              <v-icon>{{
                show ? 'mdi-chevron-up' : 'mdi-chevron-down'
              }}</v-icon>
            </v-btn>
          </v-card-actions>

          <v-expand-transition>
            <div v-show="show">
              <v-divider></v-divider>

              <v-card-text>
                {{ keterangan }}
              </v-card-text>
              <v-card-text>
                Cara Membuat :
                <br />
                {{ resep }}
              </v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Axios from 'axios'
export default {
  data: () => ({
    show: false
  }),
  props: {
    id: {
      type: String,
      default: ''
    },
    keterangan: {
      type: String,
      default: ''
    },
    resep: {
      type: String,
      default: ''
    },
    judul: {
      type: String,
      default: ''
    },
    gambar: {
      default: ''
    },
    by: {
      type: String,
      default: ''
    }
  },

  methods: {
    hapus() {
      const hapus1 = confirm('Apakah anda yakin ingin mengahapus data?')
      if (!hapus1) {
        return
      }
      const hapus2 = confirm(
        'Apakah anda benar - benar yakin ingin menghapus data ini?'
      )
      if (!hapus2) {
        return
      }
      Axios.delete('http://localhost:3001/resep/' + this.id).then((del) => {
        this.$emit('muat-ulang')
      })
    }
  }
}
</script>
