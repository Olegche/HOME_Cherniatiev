<template>
  <div>
      <div class="header">Тут відсотки відображаються за всі транзакції
          <br>
          <img src="https://media.giphy.com/media/cJjQGaB5cbIO3EnqZA/giphy.gif" alt="" class="img">
      </div>
    
      <div class="green" v-if="useMoney === true"> Сумма на рахунку {{ totalMoney }} </div>
     <div class="red" v-else> Сумма на рахунку {{ totalMoney }} </div>
    <div>
      <label>
        Додати гроші на рахунок
        <input type="number" v-model="addMoney" />
      </label>
      <button @click="sumMoney() + PercentAdd()">Додати</button>
    </div>
    <div>
      <label>
        Зняти гроші з рахунку
        <input type="number" v-model="minusMoney" />
      </label>
      <button @click="takeOffMoney() + PercentMinus()">Зняти</button>
      <div> Сплачено відсотків за обслуговування {{ moneyPercent }}</div>
      <hr />
      <div class="red" v-if="usd < 100">USD : {{ usd }}</div>
      <div class="green" v-else>USD : {{ usd }}</div> 
      <div class="red" v-if="eu < 100">EU : {{ eu }}</div>
      <div class="green" v-else>EU : {{ eu }}</div>

    </div>
  </div>
</template>

<script>
export default {
  name: "MoneyBank2",
  props: {
    percent: {
      type: Number,
      default: 0.03,
    },
    totalMoney: {
      type: Number,
      default: 0,
    },
  },

  data() {
    return {
      addMoney: "",
      minusMoney: "",
      moneyPercent: 0,
      useMoney: true,
    };
  },

  computed: {
    usd() {
      return (this.totalMoney / 28).toFixed(2);
    },
    eu() {
      return (this.totalMoney / 32).toFixed(2);
    },
  },

  methods: {
    sumMoney() {
      if (this.addMoney > 0) {
        this.useMoney = true;
        return (this.totalMoney =
          parseFloat(this.totalMoney) +
          parseFloat(this.addMoney) -
          parseFloat(this.addMoney) * this.percent);
      }
    },
    takeOffMoney() {
      if (
        this.minusMoney > 0 &&
        this.totalMoney - this.minusMoney - this.minusMoney * this.percent > 0
      ) {
        this.useMoney = false
              return (this.totalMoney =
          parseFloat(this.totalMoney) -
          parseFloat(this.minusMoney) -
          parseFloat(this.minusMoney) * this.percent);
      }
  
    },
    PercentAdd() {
      if (this.addMoney > 0)
        return (this.moneyPercent += parseFloat(this.addMoney) * this.percent);
    },
    PercentMinus() {
      if (
        this.totalMoney - this.minusMoney - this.minusMoney * this.percent >
          0 &&
        this.minusMoney > 0
      )
        return (this.moneyPercent +=
          parseFloat(this.minusMoney) * this.percent);
    },
  },
};
</script>

<style lang="css" scoped>
.green {
  color: rgb(24, 212, 46);
}

.red {
  color: darkred;
}
.header {
color: rgb(226, 187, 81);
}

.img {
    width: 10%;
}


</style>