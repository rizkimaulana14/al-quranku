<template>
  <div class="row mt-3">
    <div class="col-md-4 mt-4" v-for="surat in surats" :key="surat.id">
      <!-- Card -->
      <div class="card card-hover shadow">
        <div class="card-header">
          <strong>{{ surat.name }}</strong>
        </div>
        <div class="card-body">
          <div class="text-start">
            <ul class="list-group list-group-flush">
              <li class="list-group-item">
                Artinya: <strong>{{ surat.name_translations.id }}</strong>
              </li>
              <li class="list-group-item">
                Surat ke <strong>{{ surat.number_of_surah }}</strong> dalam
                <strong>Al - Qur'an</strong>
              </li>
              <li class="list-group-item">
                Jumlah ayat <strong>{{ surat.number_of_ayah }}</strong>
              </li>
              <li class="list-group-item">
                Diturunkan di <strong>{{ surat.place }}</strong>
              </li>
              <li class="list-group-item">
                Surat jenis <strong>{{ surat.type }}</strong>
              </li>
              <li class="list-group-item text-center mt-1">
                <p class="mb-2"><strong>Play Audio</strong></p>
                <audio class="rounded-pill" controls>
                  <source :src="surat.recitation" type="audio/mpeg" />
                </audio>

                <!-- Button Selengkapnya -->
                <router-link
                  class="
                    btn btn-info
                    rounded-pill
                    text-light
                    fw-bold
                    mt-2
                    shadow
                  "
                  :to="{
                    name: 'DetailSurat',
                    params: { no: surat.number_of_surah },
                  }"
                >
                  <i class="fa fa-info-circle"></i> Detail Surat
                </router-link>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CardSurat",
  data() {
    return {
      surats: [],
    };
  },
  methods: {
    setSurats(data) {
      this.surats = data;
    },
  },
  mounted() {
    var url =
      "https://raw.githubusercontent.com/penggguna/QuranJSON/master/quran.json";
    axios
      .get(url)
      .then((res) => {
        this.setSurats(res.data);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>