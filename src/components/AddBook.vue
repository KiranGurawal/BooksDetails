
<template>
  <v-row justify="center">
    <v-dialog
    v-model="dialog"
      max-width="600px">
      <v-card>
        <v-card-title>
          <span class="text-h5">User Profile</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="ID"
                  v-model="books.itemid"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Book Name"
                  v-model="books.bookName"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Author Name"
                  v-model="books.authorName"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Published On"
                  type="date"
                  v-model="books.publishedOn"
                   required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Page No"
                  v-model="books.pageNo"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-btn
            color="red"
            @click="$emit('closeDialog', false)"
          >
            Close
          </v-btn>
          <v-btn
            color="green"
            @click="saveBook()"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
<script>
export default {
  name: "AddBook",
  data(){
    return{
      books: {
        itemid:"",
        bookName:"",
        authorName:"",
        publishedOn:"",
        pageNo:"",
      },
    }
  },
  props:{
    dialog: Boolean,
    book: Array,
    itemid:Number

  },
  methods:{
    saveBook() {
      if(this.books.itemid =="" ){
      alert("required all fields")
      }
      // else if(this.books.itemid ===book.itemid){
      //   alert("allready book")
      // }
      else if(this.books.bookName=="")
      {
        alert("required all fields")
        }
        else if(this.books.authorName =="")
        {
        alert("required all fields")

        }
        else if(this.books.publishedOn ==""){
        alert("required all fields")
        } 
        else if(this.books.pageNo==""){
        alert("required all fields")
      }
      else{
      this.$emit('addBook', this.books);
      }
    },
  },
};
</script>
