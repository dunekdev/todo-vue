<template>
  <div>
    <input type="text" placeholder="todo" v-model="newItem">
    <button @click="addItem">dodaj</button>
    <TodoItem v-for="item in items" :key="item.id" :item="item" :style="style" @removeClicked="completeItem" @deleteClicked="removeItem" />
    
  </div>
</template>

<script>

import TodoItem from './TodoItem.vue'

export default {
    components: {
        TodoItem,
    },
  data(){ 
    return{
      newItem: '',
      items: []
    }
  },
  methods: {
    addItem(){
      this.items.push({title: this.newItem, completed: false, id: Math.random()})
      this.newItem = ''
    },
    removeItem(id){
      const index = this.items.findIndex(el => el.id === id)
      this.items.splice(index,1);
    },
    completeItem(id){
      const index = this.items.findIndex(el => el.id === id)
      this.items[index].completed = true
    }
  }
}
</script>

<style>
  .item {
    border: 1px solid #cdcdcd;
    margin: 10px;
    padding: 10px;
  }

  .completed h2 {
    text-decoration: line-through;
  }
</style>
