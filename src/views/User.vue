<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Id</th>
          <th class="text-left">Name</th>
          <th class="text-left">Email</th>
          <th class="text-left">Phone</th>
          <th class="text-left">City</th>
          <th class="text-left">Zipcode</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.email }}</td>
          <td>{{ item.phone}}</td>
          <td>{{item.address.city}}</td>
          <td>{{item.address.zipcode}}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>
<script>
import axios from 'axios';
export default {

  name: "User",
  data() {
    return {
      data: [],
    };
  },
   async mounted(){
        let fetchData = await axios.get("https://jsonplaceholder.typicode.com/users")
         //console.log(fetchData.data)
         this.data = fetchData.data
    }
};
</script>
