<template>
  <v-container fluid class="ma-0 pa-0">
    <v-layout column>
      <!-- SEARCH -->
      <v-flex class="search light-blue darken-4">
        <v-layout column align-center>
          <!-- heading -->
          <v-flex xs12 sm6 md3>
            <h1 class="display-4 white--text text-xs-center my-4 font-weight-thin">Book Finder</h1>
            <h2 class="headline white--text text-xs-center mb-4 font-weight-thin">Search'n discover</h2>
          </v-flex>
          <!-- ERROR MESSAGES -->
          <v-flex class="error-text ma-2">
            <p class="white--text" v-if="error">{{ error }}</p>
          </v-flex>
          <!-- search bar -->
          <v-flex xs12 sm6 md3>
            <v-text-field
              solo
              v-model="input"
              @click:append.prevent="search"
              @keyup.enter="search"
              append-icon="search"
              autofocus
              placeholder="What are you looking for?"
              type="text"
            ></v-text-field>
          </v-flex>
          <v-flex class="result my-2">
            <!--  - output total books -->
            <p class="white--text text-xs-center" v-if="totalBooks > 0">
              Your search returned {{ totalBooks }} books!
              <br>
            </p>
          </v-flex>
        </v-layout>
      </v-flex>

      <!--RESULT  -->

      <v-flex class="result my-4">
        <!-- pass down props -->

        <Book :books="books"></Book>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
// @ is an alias to /src
import Book from "@/components/Book.vue";
import axios from "axios";

export default {
  components: {
    Book
  },
  data() {
    return {
      input: "".trim(),
      APIURL: "https://www.googleapis.com/books/v1/volumes?q=",
      error: "",
      books: [],
      totalBooks: 0
    };
  },
  methods: {
    search() {
      //check for empty string
      if (this.input == "") {
        return (this.error = "You must give something to get something ;)");
      } else {
        axios
          .get(this.APIURL + this.input)
          .then(response => {
            //books to list
            this.books = response.data.items;

            //get total amount of books matching search criteria
            this.totalBooks = response.data.totalItems;
            this.input = "";
          })
          .catch(error => {
            // handle errors
            this.error = error.message;
            console.log(error);
          });
      }
    }
  }
};
</script>
<style>
.search {
  height: 60vh;
}
</style>
