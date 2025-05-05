<template>
  <div class="coin-table">
    <h3 class="table-title">
      <i class="header-icon fas fa-circle-dollar-to-slot"></i> Portfolio
      Breakdown
    </h3>
    <table>
      <thead>
        <tr>
          <th>Coin</th>
          <th>Symbol</th>
          <th>Price</th>
          <th>Holdings</th>
          <th>Value</th>
          <th>24h Change</th>
          <th>7d Change</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="coin in coins" :key="coin.symbol">
          <td class="coin-cell">
            <img :src="coin.icon" alt="icon" class="coin-icon" />
            {{ coin.name }}
          </td>
          <td>{{ coin.symbol }}</td>
          <td>{{ coin.price }}</td>
          <td>{{ coin.holdings }}</td>
          <td>{{ coin.value }}</td>
          <td
            :class="{
              positive: isPositive(coin.change24h),
              negative: !isPositive(coin.change24h),
            }"
          >
            {{ coin.change24h }}
          </td>
          <td
            :class="{
              positive: isPositive(coin.change7d),
              negative: !isPositive(coin.change7d),
            }"
          >
            {{ coin.change7d }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "CoinTable",
  props: {
    coins: Array,
  },
  methods: {
    isPositive(change) {
      return !change.startsWith("-");
    },
  },
};
</script>

<style scoped>
.coin-table {
  background: #2e3348;
  padding: 1rem;
  border-radius: 8px;
  border: 1px solid rgba(193, 191, 214, 0.2);
  color: #c1bfd6;
  font-family: "Rajdhani", sans-serif;
  overflow-x: scroll;
  scrollbar-width: thin;
  scrollbar-color: #c1bfd6 transparent;
  -ms-overflow-style: -ms-autohiding-scrollbar;
}

.table-title {
  margin-bottom: 1rem;
  font-size: 1.1rem;
  text-transform: uppercase;
  color: white;
  display: flex;
  align-items: center;
}

.header-icon {
  color: orange;
  font-size: 1.2rem;
  margin-right: 5px;
}

table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.95rem;
}

th {
  text-align: left;
  padding: 0.5rem;
  color: #a9a6c1;
  text-transform: uppercase;
  font-size: 0.85rem;
  border-bottom: 1px solid #3a4254;
}

tbody tr:hover {
  background: #353a4f;
  cursor: pointer;
}

td {
  padding: 0.5rem;
  border-bottom: 1px solid #3a4254;
}

.coin-cell {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.coin-icon {
  width: 20px;
  height: 20px;
  border-radius: 50%;
}

.positive {
  color: #4caf50;
}
.negative {
  color: #f44336;
}
</style>
