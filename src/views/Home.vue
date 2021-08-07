<template>
  <div class="home">
    <div class="mt-5">
      <div class="text-center">
        <h3><strong>Kumpulan Surat dalam Al - Qur'an</strong></h3>
        <CardSurat />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import CardSurat from "@/components/CardSurat";

export default {
  name: "Home",
  components: {
    CardSurat,
  },
};
</script>
