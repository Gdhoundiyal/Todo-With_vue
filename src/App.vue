<script>
import { ref } from "vue";
import ChildComponent from "./components/TheHeader.vue";
import FormComponent from "./components/Form.vue";

export default {
  name: "RootComponent",
  components: {
    ChildComponent,
    FormComponent,
  },
  data() {
    return {
      inputvalue: [],
      items: [],
    };
  },
  methods: {
    add() {
      if (this.inputvalue.length > 0) {
        this.items.push({
          id: this.items.length + 1,
          name: this.inputvalue,
        });
      } else {
        alert("Type Todo first");
      }

      this.inputvalue = "";
    },

    deleteItem(itemId) {
      this.items = this.items.filter((item) => item.id !== itemId);
      console.log("delete Item", this.items);
    },
  },
};
</script>

<template>
  <div class="Root">
    <div id="container">
      <h2 class="TodoHeading">To do List</h2>
      <div class="inputContainer">
        <input
          placeholder="Write something"
          v-model="inputvalue"
          class="todoinput"
        />
        <button @click="(event, index) => add(event, index)" class="btn">
          Add todo
        </button>
      </div>
      <ul class="ListItem">
        <li class="item" v-for="(item, index) in items" :key="index">
          <p class="todoText">{{ item.name }}</p>
          <button @click="() => deleteItem(item.id)" class="btn">delete</button>
        </li>
      </ul>
    </div>
    <!-- <ChildComponent  username="hello from Parent" /> -->
    <!-- <FormComponent/> -->
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
  width: 35vw;
  background: darkgray;
  text-align: center;
  padding: 20px;
}
.todoHeading{
  font-size: 35px;
    margin-top: 10px;
    margin-bottom: 10px;
}

.todoinput {
  padding: 10px;
  margin: 30px;
  border-radius: 5px;
  font-size: 20px;
}
.ListItem {
  list-style: none;
  padding: 0;
}
.item {
  border-radius: 5px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.todoText {
  width: 15rem;
  text-align: start;
  /* border: 1px solid; */
  font-size: 23px;
  padding: 8px;
  border-radius: 5px;
  margin: 10px;
  color: black;
  /* background-color: rgb(149, 222, 104); */
}
.btn {
  border-radius: 5px;
  padding: 9px;
  font-size: 20px;
}
</style>
