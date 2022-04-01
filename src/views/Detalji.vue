<template>
  <div class="about">
    {{ name }}
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      Autori -> {{ book.authors }}
    </li>
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      ISBN -> {{ book.isbn }}
    </li>
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      Broj stranica -> {{ book.numberOfPages }}
    </li>
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      Izdavač -> {{ book.publisher }}
    </li>
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      Zemlja podrijetla -> {{ book.country }}
    </li>
    <li v-for="book in books" v-if="book.name == name" v-bind:key="book.name">
      Broj likova -> {{ book.characters.length }}
    </li>
    <form>
      <input type="button" value="Go back!" onclick="history.back()" />
    </form>
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
