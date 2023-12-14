<template>
  <div>
    <button @click="fetchData">Récupérer des données de la base de données</button>
    <ul>
      <li v-for="data in databaseData">{{ data.REFERENCE }} {{ data.CURRENCY }} {{ data.PRICE }} {{ data.COUNTRY }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      databaseData: [],
    };
  },
  methods: {
    fetchData() {
      axios.get('http://localhost:3000/api/data') // Assurez-vous que l'URL correspond à votre backend
        .then(response => {
          this.databaseData = response.data;
          console.log(response.data)
          // response.data.forEach(e => {
          //   // console.log(e)
          // });
        })
        .catch(error => {
          console.error('Erreur lors de la récupération des données', error);
        });
    },
  },
};
</script>
