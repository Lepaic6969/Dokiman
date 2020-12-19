<template>
  <div id="UserBalance">
     <h2>{{username}}</h2>
     <h2>Su información es la siguienta: <span> {{balance}} COP </span> </h2>
  </div>
</template>

   <script>
   import axios from 'axios';
   export default {
      name: 'UserBalance',
      data: function (){
       return {
                username: "",
                name:"",
                last_name:"",
                documentos:{}
             }
       },

created: function(){
   this.username = this.$route.params.username
   let self = this
   axios.get("https://dokiman.herokuapp.com//user/balance/" + this.username)
      .then((result) => {
          self.balance = result.data.name
      })
      .catch((error) => {
             alert("ERROR Servidor");
       });
  }
}
</script>

<style>
    #UserBalance{
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        }

    #UserBalance h2{
        font-size: 50px;
        color: #283747;
        }
    #UserBalance span{
        color: crimson;
        font-weight: bold;
        }
</style>