<script>
export default {
  props:['data']
}
</script>

<template>
  <div class="container p-0" >
    <div class="d-flex" >
      <div class="card main-div w-100">
        <div class="p-3">
          <h2 class="mb-1 day">Tuesday</h2>
          <p class="text-light date mb-0">00</p>
            <small>time</small>
            <h4 class="place "><i class="fa fa-location">{{ data.location.name }} <small>{{ data.location.country }}</small></i></h4>
          <div class="temp">
            <h1 class="weather-temp font-monospace fw-bold">{{data.current.temp_c}}&deg;</h1>
              <h2 class="text-light">{{ data.current.condition.text }}</h2>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>
