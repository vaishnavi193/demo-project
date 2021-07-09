<template>
  <v-app id="app">
    <v-app-bar
      absolute
      color="#43a047"
      dark
      shrink-on-scroll
      prominent
      src="https://picsum.photos/1920/1080?random"
      fade-img-on-scroll
      scroll-target="#scrolling-techniques-5"
      scroll-threshold="500"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props" 
          gradient="to top right, rgba(55,236,186,.7), rgba(25,32,72,.7)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-app-bar-title>WEATHERAPP project</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-text-field
          placeholder= "SEARCH"
          prepend-inner-icon="mdi-magnify"
        
            
          filled
          dense
          v-model= "query"
          @change= "fetchWeather"
          
          ></v-text-field>

       
      </v-app-bar>
    </v-app>
    </template>
    
    <script>
  export default {
  name: 'app',
  data () {
    return {
      api_key: 'f534c08db9d0b67a1b68b56fc494dddd',
      
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {} ,
     city:null,


    }
  },
  methods: {
    fetchWeather (e) {
      if (e.key == "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
    setResults (results) {
      this.weather = results;
    },
    
  }
}
</script>
