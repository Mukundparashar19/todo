<script setup>
import { ref } from 'vue';

const showInput = ref(false)
const note = ref("")
const content = ref([])

const inputTodo = ()=> {
  content.value.push({
    id: Math.random(),
    text: note.value,
    date: new Date()
  })
  showInput.value = false
  note.value = ""
}

</script>

<template>
  <div class="container">     
  <main>
    <p>Todo List</p>
    <button @click="showInput = true">Add</button>
  </main>

  <!-- popup card -->
  <div  v-if="showInput"  > 
  <div class="showCard">
    
    <textarea v-model="note" name="note" id="note" cols="30" rows="10"></textarea>
    <button @click="inputTodo">push</button>
    <button @click="showInput = false">Exit</button>
  </div>
</div>

  <!-- page card -->
  <div class="card-container">
  <div v-for="i in content" :key="i.id" class="pageCard">
    <p > {{ i.text }} </p>
    <p>{{ i.date }}</p>
  </div>
 </div>
</div>
</template>

<style scoped>
main {
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

main button {
  background-color: #04AA6D;
  /* Green */
  border: none;
  color: white;
  border-radius: 50%;
  padding: 15px 30px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.card-container{
  display: flex;
flex-wrap: wrap;
}
.pageCard {
  margin: 5px;
  width: 320px;
  padding: 20px;
  border: 1px solid #c9c9c9;
  color: #04AA6D;
}


.container {
  width: 1000px;
  padding: 20px;
  margin-left: 18%;
}

.showCard{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
  border: 3px solid green;
}

.showCard textarea {
  width: 800px;
  height: 150px;
  border: 3px solid green;
}

.showCard button {
  background-color: green;
  /* Green */
  border: none;
  color: white;
  padding: 15px 30px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>