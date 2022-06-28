<template>
      <div>
   <h1>This is Api listing Data</h1>  
<table border="1px">
<tr>
<td>Id</td>
<td>Name</td>
<td>UserName</td>
<td>Email</td>
<td>Address-Street</td>
<td>Address-Suite</td>
<td>Address-City</td>
<td>Address-Zipcode</td>
<td>Address-Geo-Lat</td>
<td>Address-Geo-Lng</td>
</tr>

<tr v-for="item in list" :key="item.id">
<td><router-link :to="'/getdata/'+item.id">{{item.id}}</router-link></td>
<td>{{item.name}}</td>
<td>{{item.username}}</td>
<td>{{item.email}}</td>
<td>{{item.address.street}}</td>
<td>{{item.address.suite}}</td>
<td>{{item.address.city}}</td>
<td>{{item.address.zipcode}}</td>
<!-- <td>{{item.address.geo}}</td> -->
<td>{{item.address.geo.lat}}</td>
<td>{{item.address.geo.lng}}</td>


</tr>
</table>
</div>

</template>
<script>
import Vue from 'vue';
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)
export default {
name:'Postdata',
data()
{
   return{list:undefined}  
},
mounted(){
   Vue.axios.get('https://jsonplaceholder.typicode.com/users')
   .then((resp)=>{
   this.list = resp.data
     console.log(resp.data)
})
}
}
</script>