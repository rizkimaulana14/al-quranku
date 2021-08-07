<template>
  <div class="card shadow mt-5 mb-5">
    <div class="card-header">
      <strong>Detail Surat</strong>
    </div>
    <div class="card-body">
      <ul class="list-group list-group-flush">
        <li class="list-group-item">
          <div class="text-center">
            <h2 class="fw-bold">بِسْمِ اللّهِ الرَّحْمَنِ الرَّحِيْ</h2>
            <p class="fw-bold">
              Dengan menyebut nama Allah yang Maha Pemurah lagi Maha Penyayang
            </p>
          </div>
          <div class="mt-5" v-for="detail in details" :key="detail.id">
            <p class="fs-4 text-end">
              {{ detail.ar }}
            </p>
            <p class="text-start fs-5">Artinya : {{ detail.id }}</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DetailSurat",
  data() {
    return {
      details: [],
    };
  },
  methods: {
    setDetails(data) {
      this.details = data;
    },
  },
  mounted() {
    var url =
      "https://api.npoint.io/99c279bb173a6e28359c/surat/" +
      this.$route.params.no;
    axios
      .get(url)
      .then((res) => {
        this.setDetails(res.data);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>