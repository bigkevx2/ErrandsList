<template>
  <div id="app">
    <Header/>
    <AddErrand v-on:add-errand="addErrand"/>
    <ErrandList v-bind:Errands="Errands"
                v-on:del-errand="deleteErrand"
    />
  </div>
</template>

<script>
import ErrandList from "@/components/ErrandList";
import Header from "@/components/layout/Header"
import AddErrand from "@/components/AddErrand";

export default {
  name: 'App',
  components: {
    Header,
    AddErrand,
    ErrandList
  },
  data() {
    return {
      Errands: [
        {
        id: 1,
        title: "Errand One",
        completed: false
        },
        {
          id: 2,
          title: "Errand Two",
          completed: false
        },
        {
          id: 3,
          title: "Errand Three",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteErrand(id) {
      this.Errands = this.Errands.filter(todo => todo.id !== id);
    },
    addErrand(newErrand) {
      this.Errands = [...this.Errands, newErrand];
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
}

  body {
    font-family: Arial, Helvetica,sans-serif;
    line-height: 2em;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
