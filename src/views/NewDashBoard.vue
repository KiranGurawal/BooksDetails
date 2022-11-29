<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">
            Books Id
          </th>
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
          :key="item.itemid"
        > 
          <td>{{ item.itemid}}</td>
          <td>{{ item.bookName }}</td>
          <td>{{item.authorName }}</td>
          <td>{{item.publishedOn}}</td>
          <td>{{item.pageNo}}</td>
          <td><v-icon
          small
          class="mr-2"
          color="blue"
          @click="editBookDetails(item)"
          >
          mdi-pencil
          </v-icon>
          </td>
          <td>
          <v-icon
          small
          class="mr-2z"
          color="black"
          @click ="dialog1 = true , itemid = item.itemid"
          > 
          mdi-delete
          </v-icon>
         </td>
        </tr>
      </tbody>
      <div>
      <DeleteBook :book="book" :itemid="itemid" :dialog1="dialog1"  @closeDialog1 ="dialog1=false" v-if="dialog1" />
      </div>
      <div>
      <v-btn color="yellow" @click="dialog=true">New Book</v-btn>
      <AddBook :editItem="editItem" :dialog="dialog" v-on:addBook="saveBookDetails($event)" v-on:updateBook="update($event)"  @closeDialog="dialog=false" v-if="dialog"  />
      </div>

    </template>
  </v-simple-table>
</template>
<script>
import AddBook from '../components/AddBook.vue'
import DeleteBook from '../components/DeleteBook.vue'
import EditBook from '../components/EditBook.vue'
export default{
  name:'NewDashBoard', 
  components:{
    AddBook,
    DeleteBook,
    EditBook
  },
  data(){
    return{
      book :[
        {
        itemid:1,
        bookName:"The Last Chairlift",
        authorName:"John Irving",
        publishedOn:"October 18th 2022",
        pageNo:"912",  
        },
        {
        itemid:2,
        bookName:"A Scatter of Light",
        authorName:"Malinda Lo",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        },
        {
        itemid:3,
        bookName:"Hester",
        authorName:"John Irving",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        },
        {
        itemid:4,
        bookName:"Lavender House",
        authorName:"John Irving",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        },
        {
        itemid:5,
        bookName:"Jackal",
        authorName:" Erin E. Adams ",
        publishedOn:"October 18th 2022",
        pageNo:"912", 
        }
      ],
      dialog: false,
      dialog1: false,
      editItem :[]
    }
  },
  methods:{
    saveBookDetails(bookDetails) {
      this.book.unshift(bookDetails);
      this.dialog=false
    } ,
    editBookDetails(item){
      this.dialog = true;
      this.editItem = item;
      //console.log("-----",item)
      //console.log(editItem)
    },

    update(bookDetails){
      let index = this.book.findIndex(item => item.itemid === bookDetails.itemid);
      this.book.splice(index, 1, bookDetails);
      this.dialog=false
    },
  }
}
</script>