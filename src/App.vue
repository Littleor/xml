<template>
  <div id="app">
    Hello Vue!
  </div>
</template>

<script>

const axios = require('axios');
const x2js = require('x2js');

export default {
  name: 'App',
  components: {

  },
  created() {
    const x2jsone= new x2js();
    axios.get('/apis/zyapi.php',{
      params: {
        ac: 'videolist',
        t: 0,
        pg: 1,
        wd: "雷神"
      }
    })
      .then(function (response) {
        const xml=x2jsone.xml2js(response.data).rss.list.video[1].name;
        console.log(xml);

      })
  }
}
</script>

<style>


</style>
