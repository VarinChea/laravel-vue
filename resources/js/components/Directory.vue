<template>
 <br><br><br>
  <div class="container">
    <form @submit.prevent="submit" class="card">
        <div style="padding:30px" >
           <label for="name" class="form-label">Name</label>
            <input type="text" placeholder="Enter Name" class="form-control" id="name" v-model="item.name">
            <label for="tel" class="form-label">Telephone Number</label>
            <input  type="text" placeholder="Enter Telephone number" class="form-control" id="tel" v-model="item.tel">
             <br>
            <button class="btn btn-primary">submit</button>
        </div>

    </form>
    <div class="col-md-12 mt-3" v-if="lists.length >0">
        <h2 class="text-center">Telephone Numbers</h2>
        <ul class="list-group">
            <li class="list-group-item" v-for="item in lists" :key="item.id">
               {{ item.name }} | {{ item.tel }}
                <span style="float:right">
                       <button style="margin-right:10px" class="btn btn-warning btn-sm mr-2">View</button>
                       <button @click="deleteTel(item.id)" class="btn btn-danger btn-sm mr-2">Delete</button>
                </span>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>


import axios from 'axios'

export default {
    name: "Directory",
    data() {
        return {
            lists: [],
            item: {
                name: "",
                tel: ""
            },
        }
    },
    mounted(){
       this.fetchAll();
    },
    methods:{
        fetchAll(){
            axios.get('http://127.0.0.1:8000/api/tel')
            .then(res =>this.lists = res.data)
        },
        submit(){
            try{
             axios.post('http://127.0.0.1:8000/api/tel',this.item)
                .then(res=>{

                })
            }catch(e){
                console.log(e)
            }
        },
        deleteTel(id){
            try{
               axios.delete(`api/tel/${id}`)
                    .then(res=> this.fetchAll())
            }catch(e){

            }
        },



    }
}
</script>

