<template>
  <div id="app">
    <h1 class="tittle">The best bakeries</h1>
    <Bakeries :images="images"/>
    <Preview />
    <h2 class="cities-tittle">Our most popular location</h2>
    <CitiesList :cities="cities"/>
  </div>
</template>

<script>
import CitiesList from "./components/CitiesList.vue";
import Preview from "./components/Preview.vue";
import Bakeries from "./components/Bakeries.vue";

export default {
  name: "App",
  data: function() {
    return {
      bakeries: [],
      images: [],
      cities: []
    };
  },

  components: {
    CitiesList,
    Preview,
    Bakeries
  },
  methods: {

  },

  mounted () {
    fetch("http://api.dev.cakeiteasy.no/api/store/bakeries/?country_code=no")
      .then(response => response.json())
      .then(json => {
        this.bakeries = json;
        json.forEach(el => {
          if (el.image) {
            this.images.splice(-1, 0 ,`http://api.dev.cakeiteasy.no/api/store/images/${el.image.id}/?size=small_url&compress_type=webp`);
          }
        });
      });

    fetch("http://api.dev.cakeiteasy.no/api/store/cities/?country_code=no&")
      .then(response => response.json())
      .then(json => {
          this.cities = json;
        this.cities.sort(function(a, b) {
          if (a.most_popular > b.most_popular) {
            return 1;
          } else return 0;
        });
      });
  }
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
  padding: 15px 30px 40px;
  font-weight: bold;
  max-width: 900px;
}

.bakerie-img {
  width: 120px;
}

.tittle {
  margin-bottom: 5px;
  text-align: left;
  font-size: 16px;
  border-bottom: 1px solid rgb(154, 154, 169);
}

.cities-tittle {
  text-align: left;
  border-bottom: 1px solid rgb(154, 154, 169);
}
</style>