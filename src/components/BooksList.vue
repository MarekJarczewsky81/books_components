<template>
  <div>
    <ul>
      <book-item
        v-for="(book, index) in books"
        :key="index"
        :book="book"
        :index="index"
        @remove="handleRemove"
      />
    </ul>
    <p v-show="!books.length">No books...</p>
  </div>
</template>

<script>
import BookItem from './BookItem'

export default {
  name: 'BooksList',
  components: { BookItem },
  props: {
    books: {
      type: Array,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    handleRemove (index) {
      this.$emit('remove', index)
    }
  }
}
</script>
