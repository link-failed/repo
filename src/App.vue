<template>
  <main>
    <div class="container">
      <img src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=973295780,2514823914&fm=26&gp=0.jpg" />
      <h1>ToDo List</h1>
      <input 
        class="put-in"
        type="text"
        v-model="item.content" 
        placeholder="what to do..."
        autofocus
      />
      <button class="adding" @click="ItemAdd">add</button>
      <div class="quadrant">
        <ul class="e-and-i">
          <li v-for="todo in item.TodoList" :key="todo">
            {{todo}}<button @click="ItemDel(todo)" class="deleting">del</button>
          </li>
        </ul>
        <ul class="not-e-and-i">
          <li v-for="todo in item.TodoList" :key="todo">
            {{todo}}<button @click="ItemDel" class="deleting">del</button>
          </li>
        </ul>
        <ul class="e-and-not-i">
          <li v-for="todo in item.TodoList" :key="todo">
            {{todo}}<button @click="ItemDel" class="deleting">del</button>
          </li>
        </ul>
        <ul class="not-e-and-not-i">
          <li v-for="todo in item.TodoList" :key="todo">
            {{todo}}<button @click="ItemDel" class="deleting">del</button>
          </li>
        </ul>
      </div>
    </div>

  </main>
</template>

<script>

import { reactive } from 'vue'
export default {
  setup(){
    const item = reactive({
      content:'',
      TodoList: []
    })
    const ItemAdd = ()=>{
      console.log(item.content)
      item.TodoList.push(item.content)
    }
    const ItemDel = (todo)=>{
      item.TodoList.splice(item.TodoList.indexOf(todo), 1)
    }
    return {
      item,
      ItemAdd,
      ItemDel
    }
  } 
}
</script>

<style>
#app {
  font-family: 'Lato', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.quadrant {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: .5rem;
}

img{
  width: 200px;
}


body, html{
  height: 100%;
  background: white;
	font-family: 'Lato', sans-serif;
}

.container{
  display: block;
  position: absolute;
  margin: 0 auto;
  height: auto;
  width: 80%;
}

.put-in {
  border-radius: 7px;
  height: 30px;
  width: 200px;
  font-size: large;
}

.adding {
  font-size: large;
  border: 3px solid #f7dada;
  height: 36px;
  width: 50px;
  font-size: 20px;
  border-radius: 7px;
  cursor: pointer;
}

.deleting {
  border: 2px solid #f7dada;
  padding: 7px;
  font-size: 16px;
  border-radius: 100%;
  float: right;
  cursor: pointer;
}

ul {
  display: flex;
  flex-direction: column-reverse;
  width: 80%;
  margin-top: 30px;
}

li {
  color: #AAAAAA;
  display: block;
  position: relative;
  padding: 5px;
  width: 100%;
  font-size: medium;
  margin: auto;
  border-bottom: 1px solid rgb(194, 186, 186);
}

.deleting:hover{
  background-color: #f7dada;
  transition: all 0.4s linear;
}
.adding:hover{
  background-color: #f7dada;
  transition: all 0.4s linear;
}

</style>
