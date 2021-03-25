<template>
    <div>
        <h3>{{title}}</h3>  
        <ul>
          <li class="m-1" v-for="(sonido) in animal.sonidos" :key="sonido">
              {{ sonido }}
              <b-button pill
              variant="outline-success"
              size="sm"
              v-on:click="cantar(sonido)">Cantar</b-button>
          </li>          
        </ul>
    </div>  
</template>

<script>
export default {
    props: ["animal", "title", "cantar"]
}
</script>

<style>

</style>