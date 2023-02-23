<template>
  <div>
    <h1>Nuxt demo 1</h1>
    <button @click="loadProduct">Load</button>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">Brand</th>
            <th class="text-left">Model</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in products" :key="item.models">
            <td>{{ item.brand }}</td>
            <td>{{ item.models }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  // layout: 'blank',
  data() {
    return {
      movie: [{ title: 'Black Panther', Released: '2022', Genre: 'Action' }],
      products: [],
      post: '',
    }
  },
  mounted() {
    this.loadProduct()
  },
  methods: {
    async loadProduct() {
      await axios.get('http://nginx/api/f5').then((response) => {
        this.products = response.data.rSeries
        // for (let index = 0; index < response.length; index++) {
        //   const element = response[index];
        //   console.log(element)

        // }
        // console.log(this.products)
      })
    },
  },
}
</script>
