<template>
  <div class="hello">
    <ul class="tvBox">
      <li class="tvBox__item" v-for="tv in tvs" :key="tv.id">
        <p>{{tv.id}}</p>
        <p>{{tv.name}}</p>
        <p>{{tv.media_type}}</p>
        <img :src="'https://image.tmdb.org/t/p/original/'+tv.poster_path" alt="">
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      tvs: []
    }
  },
  mounted() {
    axios
      .get('https://api.themoviedb.org/4/list/7095934?page=1&api_key=150921e6e9f56b66a66c2719787303c0')
      .then(response => (this.tvs = response.data.results))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
