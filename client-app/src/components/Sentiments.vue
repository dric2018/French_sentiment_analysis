<template>
  <div>
    <p>{{ msg }}</p>
  </div>
</template>

<script>
//imports 
import axios from 'axios';

export default {
  name: 'Sentiments',
  data() {
    return {
      msg: 'Here is yout feeling!',
    };
  },

  methods: {
    getMessage() {
      const path = 'http://localhost:5000/sentiments';
      axios.get(path)
        .then((res) => {
          this.msg = res.data;
        })
        .catch((error) => {
          // eslint-disable-next-line
          console.error(error);
        });
    },
  },
  created() {
    this.getMessage();
  },
};
</script>
