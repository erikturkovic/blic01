<template>
  <div class="home">

  </div>
</template>

<script>


export default {
  name: "HomeView",
  data: function () {
    return {
      books: [],
    };
  },
  async mounted() {
    let rezultat = await fetch(
      "https://www.anapioficeandfire.com/api/books"
    );
    let podaci = await rezultat.json();
    console.log(podaci);
    this.books = podaci;
  },
};
</script>
