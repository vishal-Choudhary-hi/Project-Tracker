<template>
  <h1>Edit Project</h1>
  <form @submit.prevent="handleSubmit">
    <label>Title :</label>
    <input type="text" required v-model="title">
    <label>Details :</label>
    <textarea required v-model="details"></textarea>
    <button>Update Project</button>
  </form>
</template>

<script>
export default {
  data(){
    return{
      title:'',
      details:'',
      url:'http://localhost:3000/project/' + this.id,
    }
  },props:['id'],
  mounted(){
    fetch(this.url)
    .then(res => res.json())
    .then(data=>{
      this.title = data.title
      this.details=data.details
    })
  },methods:{
    handleSubmit(){
      fetch(this.url,{
        method:'PATCH',
        headers:{'Content-Type':'application/json'},
        body: JSON.stringify({title:this.title,details:this.details}),
      }).then(()=>{
        this.$router.push('/')
      })
      .catch(err=>consle.lod(err.message))
    }
  }
}
</script>

<style>
  form{
        background-color:white;
        padding:20px;
        border-radius:10px;
    }
    label{
        display:block;
        color:#bbb;
        text-transform:uppercase;
        font-size:14px;
        font-weight: bold;
        letter-spacing: 2px;
        margin: 20px 0 10px 0;
    }
    input{
        padding:10px;
        border:0;
        border-bottom: 1px solid #ddd;
        width: 100%;
        box-sizing: border-box;
    }
    textarea{
        border-bottom: 1px solid #ddd;
        padding:10px;
        width: 100%;
        box-sizing: border-box;
        border-radius:6px;
        height: 100px;
    }
    form button{
        display: block;
        margin: 20px auto 0;
        background: #00ce89;
        color:white;
        font-size:16px;
        border-radius: 6px;
        border:0;
        padding:10px;
    }
</style>