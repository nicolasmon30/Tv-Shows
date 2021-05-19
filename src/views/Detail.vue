<template>
    <div class="tvContainer tvContainer--limit">
        <div class="tvDetail">
            <div class="tvDetail__poster">
                <div class="tvDetail__poster__box">
                    <div class="tvDetail__poster__thumbnail">
                        <img :src="'https://image.tmdb.org/t/p/original/'+tvDetail.poster_path" alt="">
                    </div>
                    <div class="tvDetail__poster__name">
                        <h3>{{tvDetail.name}}</h3>
                    </div>
                </div>
            </div>
            <div class="tvDetail__info">
                <h2>Seasons</h2>
                <div class="tvDetail__info__seasons">
                    <div v-for="(season , index) of seasons" :key="season.id" class="tvDetail__info__seasons__box">
                        <div class="tvDetail__info__seasons__box__title" @click="accordionSeason(season.id)">
                            <h3><span>{{index + 1 }}</span> {{season.name}}</h3>
                        </div>
                        <div class="tvDetail__info__seasons__box__content" v-if="season.show">
                            <h4>Aired on <strong>{{ season.air_date | shortDate }}</strong></h4>
                            <p>{{season.overview}}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: "Detail",
    data() {
        return{
            tvDetail: [],
            seasons: []
        }
    },
    async mounted(){
        let path = this.$route.params.path;
        this.tvDetail = await axios
      .get("https://api.themoviedb.org/3/tv/"+ path +"?api_key=150921e6e9f56b66a66c2719787303c0&language=en-US")
      .then(response => (response.data))
      this.seasons = this.tvDetail.seasons
      console.log("Detail", this.tvDetail)
    },
    methods:{
        accordionSeason(seasonID){
          this.seasons = this.seasons.map((season) => {
              if(season['id'] === seasonID) season.show = !season.show
              return season
          })
        }
    }

}
</script>