<template>
  <div class="container">
    <div class="menu">
      <Button
        id="sortButton"
        :btnName="'Sort Title'"
        v-on:buttonClicked="sortTitle()"
      />
      <Button
        id="sortButton"
        :btnName="'Sort Rank'"
        v-on:buttonClicked="sortRank()"
      />
      <input type="text" placeholder="Search Title" v-model="findTitle">
    </div>
    <table>
      <tr>
        <th>{{column_1}}</th>
        <th>{{column_2}}</th>
        <th>{{column_3}}</th>
        <th>{{column_4}}</th>
        <th>{{column_5}}</th>
      </tr>
      <tr class="content" v-for="(data, index) in filterTitle" :key="index">
        <td class="title">{{data.title}}</td>
        <td>{{data["imdb-id"]}}</td>
        <td>{{data.rank}}</td>
        <td>{{data.rating}}</td>
        <td>{{data["rating-count"]}}</td> 
      </tr>
    </table>
  </div>
</template>

<script>
import json from '../assets/json/movies.json'
import Button from '../components/Button'

  export default {
    name: 'Table',
    components: {
      Button
    },

    data() {
      return {
        movies: json,
        findTitle: ''
      }
    },

    props: {
      column_1: String,
      column_2: String,
      column_3: String,
      column_4: String,
      column_5: String
    },

    methods: {
      sortTitle: function() {
        return this.movies.sort((x, y) => x.title < y.title ? -1 : 1);
      },

      sortRank: function() {
        return this.movies.sort((x, y) => x.rating > y.rating ? -1 : 1);
      }
    },

    computed: {
      filterTitle: function() {
         return this.movies.filter(movie => {
          return movie.title.toLowerCase().indexOf(this.findTitle.toLowerCase()) > -1
      })
      }
    }
  }
</script>

<style scoped> 
.container {
  width: 90vw;
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.menu {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  padding-bottom: 20px;
}

#sortButton {
  margin-right: 0.5vw;
}

input[type="text"] {
  width: 23vw;
  padding: 5px;
  border-radius: 5px;
  border: 1px solid var(--black)
}

input[type="text"]:focus {
  border: 2px solid var(--darkblue)
}

.title {
  width: 30vw;
}

table {
  border: 1px solid var(--lightgrey);
  border-collapse: collapse;
}

th {
  padding: 20px 15px;
  text-align: left;
  font-weight: 700;
  font-size: 0.75em;
  color: var(--darkblue);
  text-transform: uppercase;
  background-color: var(--lightgrey);
}

td {
  padding: 15px;
  text-align: left;
  vertical-align: middle;
  font-weight: 300;
  font-size: 0.75em;
  color: var(--white);
  border-bottom: solid 1px var(--lightgrey);
}

tr, th {
  text-align: left;
  width: 15vw;
}

tr:hover {
  background-color: var(--lightgrey);
}
</style>