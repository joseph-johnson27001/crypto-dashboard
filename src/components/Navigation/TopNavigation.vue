<template>
  <div class="top-nav">
    <div class="left-section">
      <span class="brand">Crypto Exchange</span>
    </div>
    <div class="right-section">
      <i class="fas fa-bars"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopNavigation",
};
</script>

<style scoped>
.top-nav {
  display: none;
  background-color: #2e3348;
  color: #c1bfd6;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid rgba(193, 191, 214, 0.2);
  font-family: "Rajdhani", sans-serif;
  width: 100%;
  height: 40px;
  margin-bottom: 20px;
  margin-left: -20px;
  margin-right: -20px;
  margin-top: -20px;
  width: 100dvw;
  padding-top: 5px;
  height: 50px;
}

.left-section {
  display: flex;
  align-items: center;
  padding-left: 20px;
}

.left-section i {
  font-size: 20px;
  cursor: pointer;
  color: orange;
}

.brand {
  font-size: 1.25rem;
  color: orange;
  font-weight: 500;
}

.right-section i {
  font-size: 20px;
  cursor: pointer;
  padding-right: 20px;
}

@media (max-width: 699px) {
  .top-nav {
    display: flex;
  }
}
</style>
