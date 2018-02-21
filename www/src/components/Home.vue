<template>
  <div class="container">
    <div class="text-center p-3">
      <img src="//placehold.it/1000x250" alt="">
    </div>
    <div class="row">
      <div class="col">
        <div class="card">
          <slap></slap>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <slap></slap>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <slap></slap>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <slap></slap>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import slap from './Slap.vue'
  export default {
    components: {
      slap
    }
  }
</script>