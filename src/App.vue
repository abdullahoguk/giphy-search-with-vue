<template>
  <div id="app">
    <div class="header">

      <a href="/"><h1 class="title" >GiphySearch.vue</h1> </a> 

      <Search @search="showSearchResult"></Search>
    </div>
          <h3 class="subtitle">Results for <span>{{title}}</span>...</h3>

    <Preview :gifs = gifs :title=title></Preview>
    <h1 v-if="isLoading" class="loading">Loading...</h1>
  </div>
</template>


<script>
  import Search from './components/Search';
  import Preview from './components/Preview';
  import gifs50 from './assets/50gifs.json'

  export default {
    name: 'App',
    components: {
      Search, Preview
    },
    data(){
      return {
        gifs:[],
        isLoading:true,
        apiKey:"YOURGIPHYAPIKEY",
        title:"Cats"
      };
    },
    methods:{
      showSearchResult(query, num){
          this.gifs=[];
          this.isLoading = true;
          fetch(`http://api.giphy.com/v1/gifs/search?q=${query}&api_key=${this.apiKey}&limit=${num}`)
            .then((res)=>{return res.json()})
            .then((res)=>{
              this.title = query;
              this.gifs = res.data;
              this.isLoading = false;
            });
      }
    },
    created(){
      fetch(`http://api.giphy.com/v1/gifs/search?q=cats&api_key=${this.apiKey}&limit=15`)
        .then((res)=>{console.log(gifs50);return res.json()})
        .then((res)=>{
          this.gifs = res.data;
          this.isLoading = false;
        });
    }  
  };
</script>

<style>
*{
  margin: 0px;
  padding: 0px;
  text-decoration: none;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}


.header{
  display: flex;
  flex-direction: row;
  align-items: stretch;
  justify-content: space-between;
  text-align: start;
  background-color: springgreen;
  padding: 2em;
}

.title{
  margin-left: 1em;
  color: rgb(5, 107, 54);
}

.subtitle{
  
  text-align: start;
  background-color: rgb(46, 248, 131);
  padding: .5em 3em;

  color: rgb(5, 107, 54);
  font-weight: 300;
}

.subtitle span{
  color: rgb(4, 82, 42);
  font-weight: 600;
}

.title:hover{
  margin-left: 1em;
  color: rgb(0, 80, 39);
}

.loading{
  font-size: 4em;
  color:rgb(182, 182, 182);
  margin: auto;
  height: 75vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
