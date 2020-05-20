<template>
<div id="new">
  <h3>{{query}}</h3>
  <input type="text" v-model="query" placeholder="search for news">
  <div class="hello">
    <div v-for="article in articles" :key="article.id" class="container">
      <div class="card">
        <h3>{{article.title}}</h3>
        <img :src="article.urlToImage" alt />
        <p class="author">{{article.author}} {{article.publishedAt}}</p>
        <p>{{article.description}}</p>
        <br>
        <a :href="article.url" target="_blank">Read More</a>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "News",
  data() {
    return {
      msg: "news app",
      articles: "articles",
      image: "image",
      query:''
    };
  },
  mounted() {
    axios
      .get(
        "https://newsapi.org/v2/everything?q=sports&apiKey=4b8b39c67c384341a2fcad0f266e0efd"
      )
      .then(res => {
        console.log(res.data.articles);
        this.articles = res.data.articles;
      });
  }
};
</script>

<style scoped>
.hello{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 100vw;
  align-items: center;
  justify-content: center;
}
.card{
  width: 20vw;
  margin: 10px;
}


img{
  width:20vw;
}
a{
  background: rgb(151, 151, 228);
  text-decoration: none;
  color: white;
  padding: 15px;
  display: flex;
  align-self: flex-end;
  justify-content: center;
}
h3{
  margin-top: 20px;
  text-align: center;
}
input{
  width: 90vw;
  outline: none;
  padding: 20px;
  margin-left: 50px;
}
.author{
  font-weight: bold;
}
@media(max-width: 768px){
  .hello{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100vw;
  }
  img{
    width: 70vw;
  }
  .card{
    width: 70vw;
  }
}
</style>
