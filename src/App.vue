<template>
   <div>
      <input type="text" v-model="search">
      <ul>
         <li v-for="(data,index) in searchFil">
            {{ data.userId }} - {{ data.title}}
         </li>
      </ul>
   </div>
</template>

<script>
export default {
   name: 'app',
   components: {

   },
   data () {
      return {
         msg: 'Welcome to Your Vue.js App',
         datas: [],
         search: ""
      }
   },
   created() {
      this.$http.get("http://jsonplaceholder.typicode.com/posts").then((data) => {
         this.datas = data.body
         console.log(data.body)
      }).catch((err)=>{
         console.log("err")
      })

   },
   computed: {
      searchFil: function() {
         return this.datas.filter((math) => {
            return math.title.match(this.search)
         })
      }
   }

   }
</script>

<style>

</style>
