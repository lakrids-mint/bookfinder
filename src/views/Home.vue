<template>
  <v-container fluid class="ma-0 pa-0">
    <v-layout column>
      <!-- SEARCH -->
      <v-flex  class="search amber darken-1">
        <v-layout column align-center>
          <!-- heading -->
          <v-flex xs12 sm6 md3>
            <h1 class="display-4 white--text text-xs-center my-4">Book Finder</h1>
            <h2 class="headline white--text text-xs-center mb-4">Search & discover</h2>
          </v-flex>
          <!-- search bar -->      
           <v-flex  xs12 sm6 md3>
           
                   <v-text-field
            solo
           @click:append
           append-icon="search"
            clear-icon
            autofocus
            background-color="white"
            clear-icon="mdi-close-circle"
            clearable
            placeholder="What are you looking for?"
            type="text"
          ></v-text-field>
        </v-flex>
        <!-- ERROR MESSAGES -->
        <v-flex class="error-text">
        </v-flex>
       </v-layout>
      </v-flex>

 <!--RESULT  -->

       <v-flex class="result my-4" >
        <v-layout row wrap justify-center>
          <v-flex xs12 sm6 md3 class="ma-4">
            <v-card >
              <v-layout>
                <!-- IMAGE -->
                <v-flex>
                  <v-img src="https://placekitten.com/g/200/300" class="full-width"></v-img>
                </v-flex>
                <!-- CONTENT -->
                <v-flex class="book-details">
                   <v-card-title>
                       <h2 class="title font-weight-regular">title</h2>
                       <p class="font-weight-light" >by author</p>
                       <p class="font-weight-light" >publisher</p>            
                   </v-card-title>
                   <v-card-actions>
                      <v-spacer></v-spacer>
                      <v-btn flat color="orange"><v-icon>arrow_right</v-icon></v-btn>
                   </v-card-actions>
                </v-flex>
              </v-layout>
              </v-card>
          </v-flex>
          
        </v-layout>
      </v-flex>
    </v-layout>    
  </v-container> 
</template>

<script>
// @ is an alias to /src
import Book from "@/components/Book.vue";

export default {
  name: "home",
  components: {
    Book
  }
};
</script>
<style>
.search{
height: 50vh;}

.book-details{
     
    display:flex;
    flex-direction:column;
     
  
 
}
.book-details > * {
  display:flex;
  flex-direction:column;
  align-items:flex-start;
  flex-grow: 2;
  height:100%;

}
p{
 margin-bottom:0;
}

.full-width {
}


</style>
