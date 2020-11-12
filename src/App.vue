<template>
  <div id="app">
    <div class="container">
    <div class="card" @click="loadQuote">
      <div v-if="!isLoading">
      <div style="display: flex; flex-direction: row">
        <h2>> Kanye says</h2>
      </div>
        <p>{{ quote }}</p>
      </div>
      <img class="face" v-show="isLoading" src="../public/ye.png" />
    </div>
  </div>
  </div>
</template>

<script>
import axios from 'axios';
import './index.css';

export default {
  name: 'App',
  async created() {
    await this.loadQuote();
  },
  methods: {
    async loadQuote() {
      this.isLoading = true;
      const response = await axios.get('https://api.kanye.rest');
      // uncomment to see loader
      // await new Promise(resolve => setTimeout(resolve, 1000));
      this.quote = response.data.quote;
      this.isLoading = false;
    },
  },
  data() {
    return {
      quote: '',
      isLoading: true,
    }
  },
  components: {
  }
}
</script>

<style>
</style>
