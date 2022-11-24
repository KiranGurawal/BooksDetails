<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">
            Books Name
          </th>
          <th class="text-left">
            Author Name
          </th>
          <th class="text-left">
            Published On
          </th>
          <th class="text-left">
            Page No
          </th>
          <th class="text-left">
            Edit
          </th>
          <th class="text-left">
            Delete
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in book"
          :key="item.bookName"
        > 
          <td>{{ item.bookName }}</td>
          <td>{{item.authorName }}</td>
          <td>{{item.publishedOn}}</td>
          <td>{{item.pageNo}}</td>
          <td><v-icon
          small
          class="mr-2"
          @click="dialog=true"
          >
          mdi-pencil
          </v-icon>
          </td>
          <td>
          <v-icon
          small
          @click="dialog=true"
          >
          mdi-delete
          </v-icon>
         </td>
        </tr>
      </tbody>
      <div>
      <v-btn @click="dialog=true">New Book</v-btn>
      <AddBook :dialog="dialog" v-on:addBook="saveBookDetails($event)" @closeDialog="dialog=false" v-if="dialog" />
      </div>
      <div>
        <!-- <EditBook /> -->
        <new />
      </div>
    </template>
  </v-simple-table>
</template>
<script>
import AddBook from '../components/AddBook.vue'
// import EditBook from '../components/EditBook.vue'
export default{
  name:'NewDashBoard', 
  components:{
    AddBook,
    // EditBook,
  },
  data(){
    return{
      book :[
        {
        bookName:"The Last Chairlift",
        authorName:"John Irving",
        publishedOn:"October 18th 2022",
        pageNo:"912",  
        },
        {
        bookName:"A Scatter of Light",
        authorName:"Malinda Lo",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        },
        {
        bookName:"Hester",
        authorName:"John Irving",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        },
        {
        bookName:"Lavender House",
        authorName:"John Irving",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        },
        {
        bookName:"Jackal",
        authorName:" Erin E. Adams ",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        }
      ],
      dialog: false,
    }
  },
  methods:{
    saveBookDetails(bookDetails) {
      this.book.unshift(bookDetails)
     // console.log(bookDetails, 'In parent');
    }
  },
}
</script>