<template>
    <ul>
      <li v-for="(animal,index) in animals" :key="index">
        Vrsta : {{ animal.vrsta }} , ime : {{ animal.ime}} , datum rodjenja : {{ animal.datum_rodjenja ? animal.datum_rodjenja : 'Nepoznat' }}
        <button @click="removeAnimal(index)"> Remove </button>
        <button @click="moveToTop(index)"> Move to top </button>
      </li>
    </ul>
</template>

<script>
export default {
  name: 'AnimalList',
  props: {
    msg: String
  },

  data (){
    return {
      animals: [
        { vrsta: 'pas', ime: 'Boni', datum_rodjenja: '24-09-2005' },
        { vrsta: 'slon', ime: 'Ganesh', datum_rodjenja: '06-06-2006'},
        { vrsta: 'lav', ime: 'Scar', datum_rodjenja: '05-02-2001' },
        { vrsta: 'vrana', ime: 'Ajnstajn', datum_rodjenja: '09-09-2009'},
        { vrsta: 'vuk', ime: 'Ponos', datum_rodjenja: '02-02-2001'}
      ]
    }
  },

  methods : {
    removeAnimal (index) {
      this.animals.splice(index,1)
    },

    moveToTop(index) {
      let animalCopy = this.animals[index]
      this.animals.splice(index,1)
      this.animals.unshift(animalCopy) 
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  list-style: lower-latin;
}
</style>
