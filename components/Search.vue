<template>
  <div class="header container">
    <h1>WeatherApp</h1>
    <div
      style="
        display: flex;
        justify-content: center;
        height: 80px;
        margin-top: 1rem;
      "
    >
      <div class="search-container">
        <div
          class="searchbar"
          style="display: flex; justify-content: center"
        ></div>
      </div>

      <input type="text" placeholder="Enter a location" />
    </div>
    <button class="btn-search">Search</button>
  </div>
</template>

<script setup></script>

<style scoped>
.container {
  width: 80%;
  margin: 0 auto;
  padding: 20px;
}
.header {
  background-color: #252525;
  color: #fff;
  text-align: center;
  padding: 20px;
  border-radius: 30px;
}

h1 {
  margin: 0;
}

.search-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.searchbar {
  position: relative;
  width: 50%;
}

input[type="text"] {
  width: 50%;
  height: 30px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  outline: none;
  font-size: 16px;
}

.btn-search {
  background-color: #28a745;
  color: #fff;
  border: 1px solid #28a745;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  margin-left: 10px;
  transition: background-color 0.3s ease;
}

.btn-search:hover {
  background-color: #218838;
  border: 1px solid #218838;
}
</style>
