<template>
  <div>
    <p>This is the Child Component {{ username }}</p>
    <p v-if="isright">change color</p>
    <p v-else>oh no</p>
    <button v-on:down="changeclr()">change</button>
    <div v-for="item in items" :key="item.id">
        {{ item.name }}
    </div>
    {{ keyvalu }}
  </div>
</template>
  
  <script>

export default {
  name: "ChildComponent",
  props: ["username"],
  data() {
    return {
      isright: true,
      keyvalu: "",
      items: [{id: 1,name: "alpha"},{id: 2,name: "beta"},{id: 3,name: "gama"},{id: 4,name: "sopi"}]
    };
  },
  methods: {
    changeclr(eve) {
        this.keyvalu = eve.key
    console.log('keyvalu',keyvalu)
    //   if (this.isright) {
    //     this.isright = false;
    //   } else {
    //     this.isright = true;
    //   }
   
    },
  },
};
</script>
  <style>
#right {
  color: aqua;
}
#wrong {
  color: red;
}
</style>