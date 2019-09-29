<template>
  <form v-on:submit.prevent="bookSubmit(bookData)" class action="#" method="post">
    <input v-model="bookData.bookTitle" type="text" name="title" value placeholder="Book Title" />
    <input v-model="bookData.bookAuthor" type="text" name="author" value placeholder="Book Author" />
    <div>
      <label for="finishedReading">
        Finished Reading
        <input
          name="finishedReading"
          type="checkbox"
          v-model="bookData.finishedReading"
        />
      </label>
    </div>
    <div>
      <label for="borrowed">
        borrowed
        <input name="borrowed" type="radio" v-model="bookData.ownership" value="borrowed " />
      </label>
      <label for="bought">
        bought
        <input name="bought" type="radio" v-model="bookData.ownership" value="bought" />
      </label>
    </div>
    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookTitle: "",
      bookAuthor: "",
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>

<style>
</style>
