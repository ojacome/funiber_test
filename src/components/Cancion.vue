<template>
  
      <div class="col-md-4">
        <h5>{{title}}</h5>
        <span class="mr-2" v-for="sonido in cancion" :key="sonido"> {{ sonido }}</span>
      </div>
  
</template>

<script>
export default {
    props: [ "cancion", "title" ]
}
</script>

<style>

</style>