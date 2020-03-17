<template>
  <div>
    <v-form v-model="valid">
      <v-container>
        <v-row>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.judul"
              :rules="nameRules"
              label="judul"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.keterangan"
              :rules="nameRules"
              label="keterangan"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.by"
              :rules="nameRules"
              label="by"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.resep"
              :rules="nameRules"
              label="resep"
              required
            ></v-text-field>
          </v-col>

          <v-col cols="12" md="4">
            <v-text-field
              v-model="resep.gambar"
              :rules="nameRules"
              label="gambar"
              required
            ></v-text-field>
          </v-col>
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
      Axios.post('http://localhost:3001/resep', this.resep).then((send) => {
        this.$router.push('/depan')
      })
    }
  }
}
</script>
