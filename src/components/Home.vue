<template>
  <div>
    Home Page
    <router-link to="/about">About</router-link>
    <ul>
      <li v-for="(data , index) in items" :key="index">
        {{ data.message }}
        <button v-on:click="removeList(index)">Remove</button>
      </li>
    </ul>
    <input v-model="addedNewİtem" type="text"/>
    <button v-on:click="addList">add list</button>
    <p v-if="isOkay">please fill in input</p>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      addedNewİtem: '',
      isOkay: false,
      items: [
        { id: '1', message: 'vue.js' },
        { id: '2', message: 'react.js' }
      ]
    }
  },
  methods: {
    addList: function() {
      if(!this.addedNewİtem == '') {
        this.isOkay = false;
        this.items.push({
        message: this.addedNewİtem
        })
      } else if(this.addedNewİtem.length > 0) {
        this.isOkay = false;
      }
      else {
        this.isOkay = true;
      }
      this.addedNewİtem = ''
    },
    removeList: function(id) {
      this.items.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  border-top: solid #eee 2px;
}
a {
  color: rgb(41,173,225);
}
button {
  background: transparent;
  border: 1px solid rgb(41,173,225);
}
button:active {
  color: rgb(41,173,225);
}
</style>
