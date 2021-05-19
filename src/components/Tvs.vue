<template>
    <div class="tvContainer tvContainer--limit">
        <ul class="tvBox">
            <li class="tvBox__item" v-for="tv in tvs" :key="tv.id">
                <div class="tvBox__thumbnail">
                    <img :src="'https://image.tmdb.org/t/p/original/'+tv.poster_path" alt="">
                </div>
                <div class="tvBox__name">
                    <h3><a :href="'/detail/'+tv.id">{{tv.name}}</a></h3>
                </div>
                <!-- <p>{{tv.id}}</p>
                <p>{{tv.media_type}}</p> -->
            </li>
        </ul>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'TVS',
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