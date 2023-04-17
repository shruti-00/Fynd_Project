<template>
    <div class="row">

        <div class="col-sm-4">
            <h2 align="center">Registration</h2>

            <form @submit.prevent="saveData">

                <div class="form-group" align="left">
                    <label>First Name</label>
                    <input type="text" v-model="student.firstname" class="form-control" placeholder="Employee name">
                </div>

                <div class="form-group" align="left">
                    <label>Last Name</label>
                    <input type="text" v-model="student.lastname" class="form-control" placeholder="Employwee Address">
                </div>

                <div class="form-group" align="left">
                    <label>Email</label>
                    <input type="email" v-model="student.email" class="form-control" placeholder="Mobile">
                </div>

                <div class="form-group" align="left">
                    <label>Password</label>
                    <input type="password" v-model="student.password" class="form-control" placeholder="Mobile">
                </div>

                <button type="submit" class="btn btn-primary">Save</button>
            </form>
        </div>
    </div>
</template>
  
<script>

    import Vue from 'vue';
    import  axios from 'axios';

export default {
    name: 'Register',
    data() {
        return {
            result: {},
            student:{
                        id: '',
                        firstname: '',
                        lastname: '',
                        email: '',
                        Password: ''
            }
        }
    },
    created(){
    },
    mounted(){
        console.log("mounted() called....");
    },
    methods: {
        saveData()
        {
            axios.post("http://localhost:9992/student/create",this.student)
            .then(
                ({data})=>{
                    alert("Data is saved..")
                }
            )
        }
    }
}
</script>
  
  