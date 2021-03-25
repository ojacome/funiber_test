<template>
  <div id="app" class="container my-3">    
    <div class="row mb-3">
      <Cancion :cancion="cancion1" :title="'Cancion 1'"/>
      <Cancion :cancion="cancion2" :title="'Cancion 2'"/>
      <Cancion :cancion="cancion3" :title="'Cancion 3'"/>      
    </div>    
    <hr>

    <div class="row align-items-center">
      <div class="col-md-6">
        <Animal :title="'Rana'"     :animal="rana"      :cantar="cantar"/>
        <Animal :title="'Libélula'" :animal="libelula"  :cantar="cantar"/>
        <Animal :title="'Grillo'"   :animal="grillo"    :cantar="cantar"/>        
        <hr>
      </div>

      <div class="col-md-6 text-center">      
          <h3>Reproducción</h3>
          <b-button class="mr-2" variant="outline-primary" v-for="sonido in cancionRestante" :key="sonido">
            {{ sonido }}
            <b-badge variant="light"><b-icon-music-note-beamed></b-icon-music-note-beamed> <span class="sr-only">unread messages</span></b-badge>
          </b-button>      
      </div>
    </div>
  </div>
</template>

<script>
import Animal from './components/Animal.vue';
import Cancion from './components/Cancion.vue';


export default {
  name: 'App',
  components: {
    Cancion,
    Animal
  },    
  data(){
    return{
      rana:     { sonidos : ['brr', 'birip', 'brrah', 'croac'] },            
      libelula: { sonidos : ['fiu', 'plop', 'pep'] },            
      grillo:   { sonidos : ['cric-cric', 'trri-trri', 'bri-bri'] },      
      cancion1: ['brr', 'fiu', 'cric-cric', 'brrah'],
      cancion2: ['pep', 'birip', 'trri-trri', 'croac'],
      cancion3: ['bri-bri', 'plop', 'cric-cric', 'brrah'],
      cancionRestante: []
    }
  },
  methods: {
    cantar( sonido ){
      let posicionActual = -1 ;      

      if( this.cancion1.indexOf( sonido ) !== -1 ){
        posicionActual  = this.cancion1.indexOf( sonido )
        this.cancionRestante = this.cancion1.slice(posicionActual + 1, this.cancion1.length)
      }
      else if( this.cancion2.indexOf( sonido ) !== -1 ){
        posicionActual = this.cancion2.indexOf( sonido )
        this.cancionRestante = this.cancion2.slice(posicionActual + 1, this.cancion2.length)
      }
      else if( this.cancion3.indexOf( sonido ) !== -1 ){
        posicionActual = this.cancion3.indexOf( sonido )
        this.cancionRestante = this.cancion3.slice(posicionActual + 1, this.cancion3.length)
      }    
      
      setTimeout( () => this.cancionRestante = [] , 3000);
    }
  }
}
</script>

<style>

