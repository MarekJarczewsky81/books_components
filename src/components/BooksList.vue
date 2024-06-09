<template>
  <div>
    <ul>
      <li
        :key="index"
        v-for="(book, index) in books">
          {{ book.title }}, {{ book.price }}
          <!-- <button @click="removeBook(index)">Remove</button> -->
          <button @click="$emit('remove', index)">Remove</button>
          <!--funkcja $emit: przycisk emituje do rodzica event remove, przy okazji przekazując też informacje o indeksie książki do usunięcia -->
      </li>
    </ul>
    <p v-show="!books.length">No books...</p>
  </div>
</template>

<script>
export default {
  name: 'BooksList',
  props: {
    books: {
      type: Array,
      required: true
    }
    // removeBook: {
    //   type: Function,
    //   required: true
    // }
  }
  // Skrócona wersje zapisu zapisu, bez dodatkowego obiektu
  // props: {
  //   books: Array
  // }
  // props: ['books']
}
</script>
