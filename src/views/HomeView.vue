<template>
  <div class="home">
    <h1>Autor, Knjiga, Datum izlaska</h1>
    <li v-for="book in books" v-bind:key="book.name">Ime autora = {{book.authors}}
      <router-link :to="'/book/' + book.name">, Ime knjige = {{
         book.name
        }}</router-link> , Datum izlaska = 
        {{book.released}}
    </li>
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
    let rezultat = await fetch("https://www.anapioficeandfire.com/api/books");
    let podaci = await rezultat.json();
    console.log(podaci);
    this.books = podaci;
  },
};
</script>
