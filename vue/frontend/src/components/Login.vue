<template>

    <div class="row">
        
        <div class="col-sm-4">
            <h2 align="center">Login</h2>

            <form @submit.prevent="saveData">
            
            <div class="form-group" align="left">
                <label>Email</label>
                <input type="email" v-model="student.email" class="form-control" placeholder="Mobile">
            </div>

            <div class="form-group" align="left">
                <label>Password</label>
                <input type="password" v-model="student.password" class="form-control" placeholder="Mobile">
            </div>

            <button type="Submit" class="btn btn-primary">Login</button>
            </form>
        </div>
    </div>
</template>
  
<script>
import Vue from 'vue';
import  axios from 'axios';

Vue.use(axios)
export default {
    name: 'Registration',
    data() {
        return {
            result: {},
            student:{
                        email:'',
                        password:''
            }
        }
    },
    created(){
    },
    mounted(){
        console.log("mounted() has called");
    },
    methods: {
        saveData()
        {
            axios.post("https://localhost:9992/student/login",this.student)
            .then(
                ({data})=>{
                    console.log(data);
                    try{
                        if (data.status === true)
                        {
                            alert("Login Successfully");
                            this.$router.push({ name: 'Student'})
                        }
                        else
                        {
                            alert("Login is failed")
                        }
                    }
                    catch (err)
                    {
                        alert("Error, please try again");
                    }
                }
            )
        }
    }
}
</script>
  
  