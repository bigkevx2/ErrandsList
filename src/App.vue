<template>
  <div id="app">
    <Header/>
    <AddErrand v-on:add-errand="addErrand"/>
    <ErrandList v-bind:Errands="Errands"
                v-on:del-errand="deleteErrand"
                v-on:in-basket="placeInBasket"
                v-on:move-up="moveUp"
                v-on:move-down="moveDown"
    />
    <InBasketList v-bind:in-basket="InBasket"/>
  </div>
</template>

<script>
  import Header from "@/components/layout/Header";
  import AddErrand from "@/components/AddErrand";
  import ErrandList from "@/components/ErrandList";
  import InBasketList from "@/components/InBasketList";

export default {
  name: 'App',
  components: {
    Header,
    AddErrand,
    ErrandList,
    InBasketList
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
      ],
      InBasket: []
    }
  },
  methods: {
    deleteErrand(id) {
      this.Errands = this.Errands.filter(errand => errand.id !== id);
    },
    addErrand(newErrand) {
      this.Errands = [...this.Errands, newErrand];
    },
    placeInBasket(id) {
      var object = [];
       object.push( this.Errands.filter(errand => errand.id === id));
      const obj = {
        id: object[0][0].id,
        title: object[0][0].title,
        completed: true
      };
      this.InBasket = [...this.InBasket, obj];
      this.deleteErrand(id);
    },
    moveUp(index) {
      var element = this.Errands[index];
      this.Errands.splice(index,1);
      if (index == 0) {
        index = 1
      }
      this.Errands.splice((index - 1), 0, element);
    },
    moveDown(index) {
      var element = this.Errands[index];
      this.Errands.splice(index,1);
      this.Errands.splice((index + 1), 0, element);
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
