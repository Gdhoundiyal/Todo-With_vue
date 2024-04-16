<script>
import { ref } from "vue";
import ChildComponent from "./components/TheHeader.vue";
import FormComponent from "./components/Form.vue"



export default {
  name: "RootComponent",
  components: {
    ChildComponent,
    FormComponent
  },
  data() {
    return {
      inputvalue : [],
      items: [],
    };
  },
  methods: {
    add(event, index) {
      this.count++;
      this.myVariable = "helu"
      this.items.push({
        id : this.items.length + 1,
        name: this.inputvalue
      })
      this.inputvalue = ''
      
    },
    deleteItem(itemId){
       this.items =  this.items.filter((item)=> item.id !== itemId)
        console.log("delete Item", this.items)
    }
  },
};
</script>

<template>
  <div class="Root">
    <!-- <div id="container">
      <h2 class="TodoHeading">To do List</h2>
      <input placeholder="Write something" v-model="inputvalue"/>
      <button @click="(event, index) => add(event, index)" >Add todo</button>
      <ul class="ListItem">
      <li class="item" v-for="(item, index) in items" :key="index">
       <p class="todoText"> {{ item.name }} </p> 
        <button @click="() => deleteItem(item.id)" class="btn">delete</button>
      </li>
    </ul>
    </div> -->
    <!-- <ChildComponent  username="hello from Parent" /> -->
    <FormComponent/>
  </div>
</template>
<style>
body {
  margin: 0;
  background: #f0f0f5;
}
.Root {
  height: auto;
  display: flex;
  justify-content: center;
  padding: 20px;
  align-items: center;
}
#container {
  height: auto;
  width: 50vw;
  background: white;
  text-align: center;
  padding: 30px;
}
.ListItem{
    list-style: none;
    padding: 0;
}
.item {
    border: 1px solid black;
    border-radius: 5px;
    /* margin: 10px; */
    display: flex;
    justify-content: space-evenly;
    align-items: center;
}
.todoText{
    font-size: 20px;
}
.btn{
    margin-top: 5px;
    margin-bottom: 5px;
}

</style>
