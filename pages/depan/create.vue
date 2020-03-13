<template>
  <div>
    <v-form v-model="valid">
      <v-container>
        <v-row>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.judul"
              :rules="nameRules"
              :counter="10"
              label="judul"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.keterangan"
              :rules="nameRules"
              :counter="10"
              label="keterangan"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.by"
              :rules="emailRules"
              label="by"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-text-field v-model="resep.resep" label="resep"></v-text-field>
        </v-row>
        <v-row>
          <v-file-input
            multiple
            label="tambah gambar"
            v-model="resep.gambar"
          ></v-file-input>
        </v-row>
        <v-btn small color="blue" @click.prevent="kirim">kirim</v-btn>
      </v-container>
    </v-form>
  </div>
</template>

<script>
import Axios from 'axios'
export default {
  data() {
    return {
      resep: {}
    }
  },
  methods: {
    kirim() {
      Axios.post('http://localhost:3001/resep', this.post).then((send) => {
        this.$router.push('/depan')
      })
    }
  }
}
</script>
