<template>
  <h2>{{ custumTitle }}</h2>
  <p> {{ counter}} <sub>2</sub> = {{ squereCounter }}</p>

  <div>
    <button @click="increase">
      +1
    </button>
    <button v-on:click="decrease">
      -1
    </button>
  </div>
</template>

<script>
export default {

  // props: ['title','start'],
  props: {
    title:String,
    start: {
      type: Number,
      default:100,
      // required:true
      validator( value ) {
        return value > 100 
      }
    }
  },
    name:'Counter',
    // se crea dentro de la data xq de esta manera todo el obj lo q este dentro sera reactivo (que cualquier cambio que sufra va  areaccionar acorde)
    data() {
      return {
        counter: this.start
      }
    },
    methods: {
      getSquereValue(){
        return this.counter * this.counter
      },
      increase(){
        this.counter ++ ;

      },

      decrease(){
        this.counter -- ;


      }
    },
    // estos metodos se guardan en cache haciendo mas 
    // eficiente el proceso todo metodod e estos debe tener un return
    computed: {
      //todo co
      squereCounter(){
        console.log('Metodo computado');
        return this.counter * this.counter
      },
      custumTitle(){
        // console.log('title', this.title);

        return this.title ?  this.title: 'Counter';
        

      }

      
    }

}
</script>

<style>
  button{
    background-color: #64BB87;
    border-radius: 5px;
    color: white;
    margin: 0 5px;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
    
  }

  button:hover{
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;

  }
</style>