<template>
  <!-- content flex container for result -->
  <v-layout row wrap justify-center class="my-4">
    <!-- iterating over result here -->
    <v-flex v-for="book in books" :key="book.title" xs12 sm4 md3 class="ma-1">
      <v-card fluid height="100%">
        <v-layout >
          <!-- IMAGE -->
          <v-flex class="mr-1">
           <a target="_blank" :href="book.volumeInfo.infoLink">
             <img class="cover" :src="getImage(book.volumeInfo)"/>
           </a> 
            
          </v-flex>
          <!-- CONTENT -->
          <v-flex class="book-details ">
            <v-card-title>
              <h2 class="title font-weight-regular">
                {{ book.volumeInfo.title.length < 15? book.volumeInfo.title : trimTitle(book.volumeInfo.title)  }}
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
trimTitle:function(title){
  return title.slice(0,20) + "...";

},

  }
};
</script>


<style scoped>
.book-details {
  display: flex;
  flex-direction: column;
  overflow:hidden;
}
.book-details > * {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex-grow: 2;
  height: 100%;
}

a{
  text-decoration: none;
  margin:0;
  padding:0;
  cursor:pointer;
}
.cover{
  width:100%;
  height: auto;
  width:150px; 
}

</style>
