<template>
 <div>
    <table>
      <tbody>
         <tr v-for="todo in todos" :key="todo.id">
          <td>{{todo.id}}</td>
          <td>{{todo.name}}</td>
          <td>{{todo.username}}</td>
          <td>{{todo.email}}</td>
          <td>{{todo.phone}}</td>
         </tr>
      </tbody>
    </table>
 </div>
</template>

<script>
import axios  from 'axios'


export default {
 data() {
   return {
     todos:null
   }
 },
 mounted() {
   console.log('Hola mundo desde mounted')
   this.getTodos()

 },
 methods: {
   getTodos(){
     console.log('aca va el codigo getTodos')
     axios.get('https://jsonplaceholder.typicode.com/users')
     .then(response => {
            this.todos = response.data
     }).catch(e => console.log(e))

   }
 },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
