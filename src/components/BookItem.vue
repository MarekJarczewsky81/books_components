<template>
  <li>
    {{ book.title }}, {{ book.price }}
    <!-- <button @click="removeBook(index)">Remove</button> -->
    <button @click="$emit('remove', index)">Remove</button>
    <!--funkcja $emit: przycisk emituje do rodzica event remove, przy okazji przekazując też informacje o indeksie książki do usunięcia -->
  </li>
</template>

<script>
export default {
  name: 'BookItem',
  props: {
    book: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  }
}
</script>
