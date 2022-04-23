<template>
  <h1>Vue Todo List</h1>
  <CreateItem class="create" v-on:newItem="newItem"/>
  <div id="listArea">
    <ul>
      <h2>Todo</h2>
      <li v-for:="item in listItems">
        <TodoItem v-bind:tag="item" v-on:remove="removeItem" v-on:complete="completeItem"/>
      </li>
    </ul>
    <ul>
      <h2>Complete</h2>
      <li v-for:="item in completedItems">
        <CompleteItem v-bind:tag="item" v-on:remove="removeCompleteItem" />
      </li>
    </ul>
  </div>
</template>

<script>
import CreateItem from './components/createItem.vue';
import TodoItem from './components/todoItem.vue';
import CompleteItem from './components/completeItem.vue';

export default ({
  name: 'App',
  data() {
    return {
      listItems: {},
      completedItems: {}
    }
  },
  components: {
    CreateItem,
    TodoItem,
    CompleteItem
  },
  methods: {
    newItem(tag) {
      this.listItems[tag] = tag;
    },
    removeItem(tag) {
      delete this.listItems[tag];
    },
    removeCompleteItem(tag) {
      delete this.completedItems[tag];
    },
    completeItem(tag) {
      delete this.listItems[tag];
      this.completedItems[tag] = tag;
    }
  }
});
</script>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #5c80a5;
  }

  #listArea {
    width: 45vw;
    margin: auto;
    margin-top: 5vh;
    display: flex;
    flex-direction: row;
    min-width: 525px;
    
    ul {
      border-color: #5c80a5;
      border-style: solid;
      border-width: 0.25rem;
      border-radius: 0.34rem;
      width: 20vw;
      min-width: 250px;
      margin: auto;
      height: 65vh;
    }
  }

  .create {
    margin: auto;
    text-align: center;
  }

  ul {
    position: relative;
    list-style-type: none;
    margin: 0;
    padding: 0;

    h2 {
      margin-top: -2rem;
      text-align: center;
    }
  }
  
  h1 {
    text-align: center;
  }
</style>
