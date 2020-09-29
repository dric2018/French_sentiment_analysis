<template>

  <div class="container">
      <div class="text-center">
          <h1>Analyse de sentiments</h1>
          <br>
      </div>
    
    <div class="text-center">
    <img src="../assets/bert.jpg" class="rounded-circle"  width="200" height="200" alt="image ici">
    <br><br>
    </div>

    <div class="card">
       <div class="card-header">
        Amusons-nous un peu !
      </div>
      <div class="card-body">
        <p class="card-text"> Votre commentaire relève t-il d'un sentiment <span class="text-danger">négatif</span>  ou <span class="text-success">positif</span> ?</p>
      </div>

    </div>
    <br><br>

  <div class="col text-center">
    <label for="area">Laissez un commentaire...tout ce qui vous passe par la tête</label>
    <textarea class="form-control " id="area" rows="10"></textarea>
  </div>

  <div id="sentimentsBars" style="margin-bottom:1cm">
    <canvas id="sentimentBarChart"></canvas>
  </div>


  </div>
</template>

<script>
//imports 
import axios from 'axios';

export default {
  name: 'Sentiments',
  data() {
    return {
      msg: 'Yep, I am feeling myself !',
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
