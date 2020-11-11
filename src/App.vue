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
      <img class="face" v-show="isLoading" src="https://lh3.googleusercontent.com/proxy/1UAKLBUOIq8yUpc4i2HiHdjXsjecRYDSQpjXxVAdAiKwaF0ixsBvddhtr2VP0BJ2WizZSJRtDWlP9_IVEHb1md2AOqLTrMY5ZsoHc3s_RHrzBZhE0gzw" />
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
