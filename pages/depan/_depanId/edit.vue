<template>
  <div>
    <nuxt-link :to="'/depan'">
      <button class="btn btn-md btn-primary">Kembali</button>
    </nuxt-link>

    <h1>Ubah Data</h1>
    <table>
      <input
        type="text"
        name="judul"
        v-model="resep.judul"
        placeholder="Masukkan Judul"
      />
      <br />
      <input type="text" name="by" v-model="resep.by" placeholder="by" />
      <br />
      <input
        type="text"
        name="keterangan"
        v-model="resep.keterangan"
        placeholder="keterangan"
      />
      <br />
      <input
        type="text"
        name="resep"
        v-model="resep.resep"
        placeholder="resep"
      />
      <br />
      <button class="btn btn-md btn-success" @click.prevent="edit">Edit</button>
    </table>
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
  mounted() {
    this.getDetail()
  },
  methods: {
    getDetail() {
      Axios.get(
        'http://localhost:3001/resep/' + this.$route.params.depanId
      ).then((res) => {
        this.resep = res.data || {}
      })
    },
    edit() {
      Axios.patch(
        'http://localhost:3001/resep/' + this.$route.params.depanId,
        this.resep
      ).then((send) => {
        this.$router.push('/depan')
      })
    }
  }
}
</script>
