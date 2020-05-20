<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="article in articles" :key="article.id">
      <h3>{{article.author}}</h3>
      <h6>{{article.content}}</h6>
      <p>{{article.url}}</p>
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
      url ="url"
    };
  },
  mounted(){
     axios.get('http://newsapi.org/v2/top-headlines?' +'country=us&'+'apiKey=4b8b39c67c384341a2fcad0f266e0efd')
     .then(res => {
       console.log(res.data)
     this.articles = res.data.articles
     })
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
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

img {
  width: 30vw;
  height: 30vh;
}
</style>
