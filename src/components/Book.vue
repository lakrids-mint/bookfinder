<template>
  <!-- content flex container for result -->
  <v-layout row wrap justify-center>
    <!-- iterating over result here -->
    <v-flex v-for="book in books" :key="book.title" xs12 sm6 md3 class="ma-4">
      <v-card height="100%">
        <v-layout>
          <!-- IMAGE -->
          <v-flex>
            <a target="_blank" :href="book.volumeInfo.infoLink"><img  class="cover"
            :alt="book.volumeInfo.title"
            :src="(getImage(book.volumeInfo))"/></a>
            
          </v-flex>
          <!-- CONTENT -->
          <v-flex class="book-details">
            <v-card-title>
              <h2 class="title font-weight-regular">
                {{ book.volumeInfo.title }}
              </h2>
              <p class="font-weight-light">
                by
                <!--No author? -->
                {{book.volumeInfo.authors? "":"Unknown author(s)"}}
                <span v-for="(author, index) in book.volumeInfo.authors">
                  <!-- format author list -->
                  {{author}}</span>
              </p>
              <p class="font-weight-light">
                {{ book.volumeInfo.publisher? book.volumeInfo.publisher.toUpperCase():"Publisher unknown".toUpperCase()}}</p>
            </v-card-title>
           
          </v-flex>
        </v-layout>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  props: ["books"],
  methods: {
    getImage: function(book){
            if("imageLinks" in book && "thumbnail" in book.imageLinks){
                
                return book.imageLinks.thumbnail;
            } else{
              
                return "https://placekitten.com/g/200/300";
            }
},

  }
};
</script>
<style scoped>
.book-details {
  display: flex;
  flex-direction: column;
}
.book-details > * {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex-grow: 2;
  height: 100%;
}
p {
  margin-bottom: 0;
}
a{
  text-decoration: none;
}
.cover{
  height: 100%;
  width:100%;
}
</style>
