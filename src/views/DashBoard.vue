<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="books"
      sort-by="author"
      class="elevation-1"
    >
    <!-- <Edit />
    <Rest /> -->
    </v-data-table>
    <AddBook />
  </div>
</template>
<script>
import AddBook from '../components/AddBook.vue'
// import Rest from '../components/Rest.vue'
// import Edit from '../components/Edit.vue'
export default {
  data: () => ({
    dialog: false,
    dialogDelete: false,
    books: [],
    headers: [
      {
        text: "Books name",
        align: "start",
        sortable: false,
        value: "name",
      },
      { text: "Author name", value: "author" },
      { text: "Published on", value: "published" },
      { text: "Page no", value: "page" },
      { text: "Actions", value: "actions", sortable: false },
    ],
    
  }),
  components:{
    AddBook,
    // Edit,
    // Rest,
  }, 
};
</script>
<style scoped></style>
