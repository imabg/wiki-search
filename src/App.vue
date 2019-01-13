<template>
  <div id="app">
    <h1>Wikipedia Search</h1>
    <p>Crafted By <a href="https://github.com/abhay676" class="abhay" target="__blank">Abhay Goswami😎</a></p>
    <SearchBar @search = "makeRequest"/>
    <Card :pages = "pages" :result = "result"/>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/searchBar'
import Card from './components/card'

export default {
  name: 'app',
  components: {
    SearchBar,
    Card
  },
  data() {
    return {
      pages: null,
      result: false
    }
  },
  methods: {
    makeRequest(q) {
      axios.get(`https://en.wikipedia.org/w/api.php?action=query&generator=search&gsrnamespace=0&exsentences=1&exintro&explaintext&exlimit=max&prop=extracts&gsrlimit=10&origin=*&gsrsearch=${q}&format=json`)
      .then(res => {
          this.pages = res.data.query.pages; 
          this.result = true;
      })
      .catch(err => {
        console.log('ERROR')
      })
    }
  }
 
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

  .abhay {
    text-decoration: none;
    cursor: pointer;
    color: #205A9C;
  }
</style>
