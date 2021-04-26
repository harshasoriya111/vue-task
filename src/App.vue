<template>
  <div id="app">
    <Header />
    <div class="content">
      <Table :infos="dummyData" />
      <Description />
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios';
Vue.use(axios,VueAxios);
import Header from './components/Header.vue';
import Table from './components/Table.vue';
import Description from './components/Description.vue';

export default {
  name: 'App',
  components: {
    Header,
    Table,
    Description
  },
  data() {
    return {
      dummyData : []
    }
  },
  mounted() {
    axios.get('http://localhost:3000/data')
        .then(res => {
          this.dummyData = res.data
        })
        .catch(error => {
          console.log(error);
        })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.content {
  display: flex;
}
</style>
