<template>
  <div id="app">

    <!-- heading -->
    <header>
      <h1>Books<span>.app</span></h1>
    </header>

    <!-- books list -->
    <books-list
      @remove="removeBook"
      :books="books" />

    <!-- no books message -->
      <books-length-msg :length="books.length" />
    <!-- add book form -->
    <book-form @add="addBook" />
  </div>
</template>

<script>
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg'
import BookForm from './components/BookForm'

export default {
  name: 'App',
  data: () => ({
    books: [
      {
        title: 'The Catcher in the Rye',
        price: 20
      },
      {
        title: 'Of Mice and Men',
        price: 18
      }]
  }),
  components: { BooksList, BooksLengthMsg, BookForm },
  methods: {
    addBook (book) {
      this.books.push({...book})
    },
    removeBook (index) {
      this.books.splice(index, 1)
    }
  }
}
</script>
