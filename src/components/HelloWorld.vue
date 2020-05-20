<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="article in articles" :key="article.id" class="container">
      <h3>{{article.title}}</h3>
      <p>{{article.author}}  {{article.publishedAt}} on {{article.source}}</p>
      <p>{{article.description}}</p>
      <h6>{{article.content}}</h6>>
      <a :href="article.url" target="_blank">follow link</a>
      <img :src="article.urlToImage" alt="">
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "news app",
      articles:'articles',
      image: "image",
    };
  },
  mounted(){
     axios.get('http://newsapi.org/v2/top-headlines?' +'country=us&'+'apiKey=4b8b39c67c384341a2fcad0f266e0efd')
     .then(res => {
       console.log(res.data.articles)
     this.articles = res.data.articles
     })
  },
};
</script>

<style scoped>

.hello{
 width: 100%;
 margin: 0 20%;

}
.container{
  width: 70vw;
  display: flex;
   flex-direction: column;
}
img {
  width: 70vw;
  height: 70vh;
 
}
</style>
