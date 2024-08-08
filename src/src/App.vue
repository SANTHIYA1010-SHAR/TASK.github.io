<template>
  <div id="app">
    <AssetTable />
  </div>
</template>

<script>
import AssetTable from './components/AssetTable.vue';

export default {
  name: 'App',
  components: {
    AssetTable
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
