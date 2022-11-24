
<template>
  <v-row justify="center">
    <v-dialog
    v-model="dialog"
      persistent
      max-width="600px"
    >
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
                  label="Book Name"
                  required
                  v-model="book.bookName"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Author Name"
                  required
                  v-model="book.authorName"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Published On"
                  required
                  v-model="book.publishedOn"
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Page No"
                  required
                  v-model="book.pageNo"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-btn
            color="blue darken-1"
            text
            @click="$emit('closeDialog', false)"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="saveBook();"
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
      name:"kiran",
      book: {
        bookName:"",
        authorName:"",
        publishedOn:"",
        pageNo:"",
      },
      booksArray:[],
    }
  },
  props:{
    dialog: Boolean,
  },
  methods:{
    saveBook() {
      this.$emit('addBook', this.book);
      // this.booksArray.({
      //   bookName:this.bookName,
      //   authorName:this.authorName,
      //   publishedOn:this.publishedOn,
      //   pageNo:this.pageNoInput
      // })
    },
  },
};
</script>
