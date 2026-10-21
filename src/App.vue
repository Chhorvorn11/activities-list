<template>
  <div class="parent">
    <div class="cart">
      <div class="activity">
        <input v-model="text" class="input" type="text" placeholder="What do you want to do ?">
        <button type="submit" class="btn-add" @click="handleClick">ADD</button>
      </div><br>
      <TodoList :text="text" :items="items" @remove="removeItem" @clear="items = []" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TodoList from './components/TodoList.vue';

const text = ref('')
const items = ref([])

function handleClick() {
  if (!text.value) return
  items.value.push(text.value)
  text.value = ''
}
function removeItem(index) {
  items.value.splice(index, 1)
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

.parent {
  width: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.cart{
  width: 600px;
  height: auto;
  border: 1px solid navy;
  border-radius: 16px;
  padding: 10px;
}


.input,
.btn-add {
  width: 85%;
  padding: 8px;
  background-color: antiquewhite;
  border: none;
  border-radius: 8px 0 0 8px;
}

.btn-add {
  width: 15%;
  background-color: aqua;
  border-radius: 0 8px 8px 0;
  text-align: center;
}

.btn-add:hover {
  border: 1px solid navy;
}
</style>