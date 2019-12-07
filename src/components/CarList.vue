<template>
  <div>
    <div class="page-header">
      <h2 class="title">Cars available for rent</h2>
    </div>
    <div class="content columns is-multiline">
      <div v-for="car in cars" v-bind:key="car.id" class="column is-one-quarter">
        <div class="card">
          <div class="card-image">
            <img v-bind:src="car.image">
          </div>
          <div class="card-content">
            <div class="media">
              <div class="media-content">
                <p class="title is-size-4">{{ car.name }} <span class="is-size-6 has-text-gray"> {{ car.category }}</span></p>
              </div>
            </div>
            <div class="content">
              {{ car.price }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .page-header {
    margin-bottom: 30px;
  }
</style>

<script>

import axios from 'axios';

export default {
  name: 'CarList',
  data() {
    return { cars: []}
  },
  methods: {
    async getAllCars() {
      const response = await axios.get('http://localhost:8000/cars');
      this.cars = response.data;
    }
  },
  mounted() {
    this.getAllCars();
  }
}
</script>