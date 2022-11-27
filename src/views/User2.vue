<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Id</th>
          <th class="text-left">Name</th>
          <th class="text-left">Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.email }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>
<script>
import axios from 'axios';
export default {

  name: "User2",
  data() {
    return {
      data: [],
    };
  },
  methods:{
             let add = fetch('https://jsonplaceholder.typicode.com/users')
             .then(function(response){
                return response.json();
             }).then(function(result){
                console.log(result);
             })
             console.log(add)
  }

};
</script>
