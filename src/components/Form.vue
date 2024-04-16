<template>
  <form>
    <label for="username"></label>
    <input type="text" required v-model="username" />
    <label for="password"></label>
    <input type="password" required v-model="password" />
    <button @click="formSubmit()">Submit</button>
    <button @click="showdetails()">{{ btnText }}</button>
    <div v-if="isActive">
        <p>username is {{ userdata.name }}</p>
        <p>userpass is {{ userdata.pass }}</p>
    </div>
  </form>
</template>

<script>
console.log("outer")
export default {
data(){
    return{
        userdata: { name: "",
    pass: "",},
    username: "",
    password: "",
    isActive: false,
    isdisabled: true
    };
},
methods: {
    formSubmit(){
        console.log("form Submitted", this.username, this.password, this.userdata.name)
        this.userdata.name = this.username
        this.userdata.pass = this.password
        this.username = ""
        this.password = ""
        this.btnText = "show Details"
    },
    showdetails(){
        console.log("showdetails")
        this.isdisabled = false
        this.isActive = !this.isActive;
        !this.isActive ? this.btnText = "hide details" : this.btnText = "Show details" 
    }
}
}
</script>

<style>
</style>