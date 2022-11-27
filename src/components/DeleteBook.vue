<template>
  <v-row justify="center">
    <v-dialog
      v-model="dialog1"
      max-width="290"
    >
      <v-card>
        <v-card-title class="text-h6">
          Are You Sure To Delete This Book!
        </v-card-title>
        <v-card-title ></v-card-title>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green darken-1"
            text
            @click="deleteBookDetails(itemid)"
          >
            Ok
          </v-btn>
          <v-btn
            color="green darken-1"
            text
            @click="$emit('closeDialog1', false)"
          >
            cancle
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>
<script>
export default{
  name:"DeleteBook",
  data(){
    return{
      dialog1 :""
    }
  },
  props:{
  itemid : Number,
  dialog1 : Boolean,
  book:Array
  },
  methods:{
     deleteBookDetails(itemid){
      let index = itemid-1
      console.log("item", index)
     // console.log("items", this.book)
      this.book.splice(index,1)
      this.dialog1 = false
    }
  }
}
</script>
