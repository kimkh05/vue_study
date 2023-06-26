<template>
  <TodoHeader />
  <TodoInput />
  <TodoList />
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
  name: "App",
  components: {
    TodoHeader,
    TodoInput,
    TodoList
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  outline: 0;
  box-sizing: border-box;
  border: 0;
  font-family: pretendard, sans-serif;
}

span {
  color: red;
}
</style>
