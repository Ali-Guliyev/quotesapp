<template>
  <div v-if="quote.content">
    <h3>"{{ quote.content }}"</h3>
    <p>-{{ quote.author }}</p>
  </div>
  <button @click="generateQuote()">Generate new Quote</button>
</template>

<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
  setup() {
    const quote = ref({});

    const generateQuote = async () => {
      await axios.get('https://api.quotable.io/random').then((res) => {
        quote.value = res.data;
      });
    };

    return { generateQuote, quote };
  },
};
</script>
