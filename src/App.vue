<template>
  <div id="app">
    <h1>movie rating</h1>
    <Table column_1="title" column_2="imdb-id" column_3="rank" column_4="rating" column_5="rating-count"/>
  </div>
</template>

<script>
import Table from './components/Table'

export default {
  name: 'app',
  components: {
    Table
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto+Condensed');

body {
  --white: rgb(255, 255, 255);
  --black: rgba(0, 0, 0, 0.5);
  --lightgrey: rgba(255,255,255,0.3);
  --darkblue: rgb(16, 99, 173);
  --lightblue: #25b7c4;
  --cyan: #25c481;

  font-family: 'Roboto Condensed', sans-serif;
  background: -webkit-linear-gradient(left, var(--cyan), var(--lightblue));
  background: linear-gradient(to right, var(--cyan), var(--lightblue));
}

h1 {
  text-align: center;
  text-transform: uppercase;
  color: var(--darkblue);
  text-shadow: 1px 1px var(--black);
}
</style>
