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
        count: '1',
        errand: "Product toevoegen",
        completed: false
        },
        {
          id: 2,
          count: '2',
          errand: "Product aantal opgeven",
          completed: false
        },
        {
          id: 3,
          count: '3',
          errand: "Items afvinken",
          completed: false
        },
        {
          id: 4,
          count: '4',
          errand: "Afgevinkte items komen onderaan de lijst en zijn doorgestreept",
          completed: false
        },
        {
          id: 5,
          count: '5',
          errand: "Je kunt items uit de lijst verwijderen",
          completed: false
        },
        {
          id: 6,
          count: '6',
          errand: "Je kunt de volgorde van items aanpassen",
          completed: false
        },
        {
          id: 7,
          count: '7',
          errand: "Afgevinkte items zijn grayed out",
          completed: false
        },
        {
          id: 8,
          count: '8',
          errand: "De applicatie is responsive",
          completed: false
        },
        {
          id: 9,
          count: '9',
          errand: "Het is een Single Page Application",
          completed: false
        },
        {
          id: 10,
          count: '10',
          errand: "De app is gemaakt met een zelfgekozen framework (VUE)",
          completed: false
        },
        {
          id: 11,
          count: '11',
          errand: "Per groep een verschillend framework",
          completed: false
        }
      ],
      InBasket: [],
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
        count: object[0][0].count,
        errand: object[0][0].errand,
        completed: true
      };
      this.InBasket = [...this.InBasket, obj];
      this.deleteErrand(id);
    },
    moveUp(index) {
      var element = this.Errands[index];
      this.Errands.splice(index,1);
      if (index === 0) {
        index = 1
      }
      this.Errands.splice((index - 1), 0, element);
    },
    moveDown(index) {
      let element = this.Errands[index];
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
