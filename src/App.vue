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
  <div>
    <p v-show="books.length">Actually we'have:</p>
    <p v-if="books.length > 5">{{ books.length }} books</p>
    <p v-else-if="books.length > 1 && books.length <= 5">Not too many of them...</p>
    <p v-if="books.length === 1">One single book!</p>
    <p v-if="books.length < 1">Go get some books!</p>
  </div>
    <!-- add book form -->
    <form @submit.prevent="handleSubmit">
      <label>
        Title:
        <input v-model="form.title" type="text" name="title">
      </label>
      <label>
        price:
        <input v-model="form.price" type="number" name="price">
      </label>
      <button>Add book</button>
    </form>
  </div>
</template>

<script>
import BooksList from './components/BooksList'

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
      }],
    form: {
      index: 0,
      title: '',
      price: 0
    }
  }),
  components: { BooksList },
  methods: {
    handleSubmit () {
      this.books.push({ ...this.form })
      this.form.title = ''
      this.form.price = 0
    },
    removeBook (index) {
      this.books.splice(index, 1)
    }
  }
}
</script>
