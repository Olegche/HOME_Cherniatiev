<template>
  <div>
      <h1>Restauraunt la Banosh</h1>

<h2>What do You want to eat?</h2>
      <input type="text" v-model="myDish" />
      <button @click="addDish">To place an order</button>

<div class="mainDiv">
<span class="order">
      <order :order-list="dishList" @dish-to-cooking="dishToCooking" />
    </span>

    <span class="cooking">
      <cooking :cooking-list="cookingList" @dish-to-serve="dishToServe" />
    </span>

     <span class="serve">
      <serve :serve-list="serveList" @eat="Eat" />
    </span>
</div>
    

    
  </div>
</template>

<script>
import order from "./order";
import cooking from "./cooking"
import serve from "./serve"
export default {
  name: "MainRestaurant",

  components: {
    order,
    cooking,
    serve
  },

  data() {
    return {
      myDish: null,
      dishList: ["palachiny with lekvar", "carrot Al dente ", "banosh classic"],
      cookingList: ["la bodrash", "pizza with salo only"],
      serveList: [" red borzhch", " kiwi smoothy"]

      
    };
  },

  methods: {
    addDish() {
      this.dishList.push(this.myDish);
      this.myDish = null
    },

    dishToCooking(index) {
        this.cookingList.push(this.dishList[index])
      this.dishList.splice(index, 1);
    },

    dishToServe(index) {
        this.serveList.push(this.cookingList[index])
      this.cookingList.splice(index, 1);
    },

    Eat(index) {
        this.serveList.splice(index,1)
    }
  },
};
</script>

<style lang="css" scoped>

.order {
    text-align: left;  
    padding: 10px; 
    display: inline-flex
     
}
.cooking {
    text-align: center;
    padding: 10px ;
    display:inline-flex
    
}
.serve {
    text-align: right;
    padding: 10px ;
    display: inline-flex
    
}
.mainDiv {
    width: 900px;
    border: 4px double rgb(255, 252, 83); 
    padding: 10px;
    background-color: #00DBDE;
    background-image: linear-gradient(90deg, #00DBDE 0%, #FC00FF 100%);

    margin-left: 200px;
    margin-top: 10px;
    border-radius: 30px;
}
h1 {
    color: rgb(76, 196, 243);
}

button  {
    background-color: rgb(255, 98, 80);
    border-radius: 30px;
    margin: 10px;
    color: rgb(247, 241, 246);
    width: 150px;
    height: 30px;
    font-size: 15px;
}
span {
    color: rgb(4, 4, 4);
}
</style>