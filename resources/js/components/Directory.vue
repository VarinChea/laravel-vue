<template>
  <div class="container">
    <form @submit.prevent="submit">
            <label for="name" class="form-label">Name</label>
            <input type="text" placeholder="Enter Name" class="form-control" id="name" v-model="item.name">
            <label for="tel" class="form-label">Telephone Number</label>
            <input  type="text" placeholder="Enter Telephone number" class="form-control" id="tel" v-model="item.tel">
            <button class="btn btn-primary">submit</button>
    </form>
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
    methods:{
        submit(){
            try{
             axios.post('http://127.0.0.1:8000/api/tel',this.item)
                .then(res=>{

                })
            }catch(e){
                console.log(e)
            }
        }
    }
}
</script>

