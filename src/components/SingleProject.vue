<template>
  <div class="project" :class="{complete :project.complete}">
    <div class="action">
        <h3 @click="toggle">{{project.title}}</h3>
        <div class="icons">
            <router-link :to="{name:'EditProject', params:{id:project.id}}">
                <span>Edit</span>
            </router-link>
            <span @click="deleteProject">Delete</span>
            <span class="iconDone" :class='{iconDonecomplete:project.complete}' @click="completeProject">Done</span>
        </div>
    </div>
    <div>
        <p v-if="showDetails">{{project.details}}</p>
    </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            showDetails:false,
            db:'http://localhost:3000/project/'+this.project.id,
        }
    },
    props:['project'],
    methods:{
        toggle(){
            this.showDetails=!this.showDetails
        },
        deleteProject(){
            fetch(this.db,{method:'DELETE'})
            .then(()=>this.$emit('delete',this.project.id))
            .catch(err=>console.log(err.message));
        },
        completeProject(){
            fetch(this.db,{method:'PATCH',headers:{'content-Type' : 'application/json'},
            body:JSON.stringify({complete:!this.project.complete})
            })
            .then(()=>this.$emit('complete',this.project.id))
            .catch(err=>console.log(err.message))
        }
    }
}
</script>

<style>
    .project{
        margin: 20px auto;
        background: #fff;
        padding: 10px 20px;
        border-radius:10px;
        box-shadow: 1px 2px 3px rgba(0,0,0,0.5);
        border-left:4px solid #e90074;
    }
    h3{
        cursor: pointer;
    }
    .action{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    span{
        margin-left:5px;
        font-weight:bolder;
        color:rgb(181, 180, 180);
    }
    a{
        text-decoration: none;
    }
    span:hover{
        color:rgb(95, 95, 95);
    }
    .project.complete{
        border-left:4px solid #00e908;
    }
    .iconDonecomplete{
        color:#00e908;
    }
</style>