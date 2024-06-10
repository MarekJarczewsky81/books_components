<template>
  <div>
    <form @submit.prevent="$emit('add', form), handleSubmit">
      <label>
        Title:
        <input v-model="form.title" type="text" name="title">
      </label>
      <label>
        Price:
        <input v-model="form.price" type="number" name="price">
      </label>
      <button>Add book</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'BookForm',
  data: () => ({
    form: {
      title: '',
      price: 0
    }
  }),
  methods: {
    handleSubmit () {
      this.$emit('add', this.form)
    // here is your code for emptying the form
    }
  }
}
</script>
