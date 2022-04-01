<template>
  <div class="about">
    {{ name }}
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      ISBN -> {{ book.isbn }}
    </li>
  </div>
</template>

<script>
export default {
  props: ["name"],
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
