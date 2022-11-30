<template>
  <v-row justify="center">
    <v-dialog v-model="dialogEdit" max-width="600px">
      <v-card>
        <v-card-title>
          <span class="text-h5">Edit Book</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
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
          <v-btn color="red" @click="$emit('closeDialogEdit', false)">
            Close
          </v-btn>
          <v-btn color="green" @click="editBook()"> Save </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
  <script>
export default {
  name: "EditBook",
  data() {
    return {
      book: {
        id: "",
        bookName: "",
        authorName: "",
        publishedOn: "",
        pageNo: "",
      },
    };
  },
  props: {
    dialogEdit: Boolean,
    itemid: Object,
  },
  created: function () {
    this.book = this.itemid;
  },

  methods: {
    editBook() {
      //  this.book.id = this.itemid;
      console.log(this.book);
      this.$emit("editBook", this.book);
    },
  },
};
</script>
