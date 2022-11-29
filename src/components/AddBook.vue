<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" max-width="600px">
      <v-card>
        <v-card-title>
          <span class="text-h5">User Profile</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Book Id"
                  v-model="book.itemid"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Book Name"
                  v-model="book.bookName"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Author Name"
                  v-model="book.authorName"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Published On"
                  type="date"
                  v-model="book.publishedOn"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Page No"
                  v-model="book.pageNo"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-btn color="red" @click="$emit('closeDialog', false)">
            Close
          </v-btn>
          <v-btn color="green" @click="saveBook()"> Save </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
<script>
export default {
  name: "AddBook",
  
  data() {
    return {
      book: {
        itemid: "",
        bookName: "",
        authorName: "",
        publishedOn: "",
        pageNo: "",
      },
      isUpdating: false,
    };
  },
  created: function () {
    this.book = this.editItem;
    // if (this.book == null) {
    //   this.isUpdating = false;
    // }
  },
  props: {
    dialog: Boolean,
    editItem: Array,
  },
  
  methods: {
    saveBook() {
      if (this.book.itemid == "") {
        alert("required all fields");
      }
      // else if(this.books.itemid ===book.itemid){
      //   alert("allready book")
      // }
      else if (this.book.bookName == "") {
        alert("required all fields");
      } else if (this.book.authorName == "") {
        alert("required all fields");
      } else if (this.book.publishedOn == "") {
        alert("required all fields");
      } else if (this.book.pageNo == "") {
        alert("required all fields");
      } else {
        this.$emit("addBook", this.book);
      }
    },
    updateBook() {
      this.$emit("updateBook", this.book);
    },
  },
};
</script>
