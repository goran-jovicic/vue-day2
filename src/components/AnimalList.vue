<template>
    <ul>
      <li v-for="(animal,index) in animals" :key="index">
        Vrsta : {{ animal.vrsta }} , ime : {{ animal.ime}} , datum rodjenja : {{ animal.datum_rodjenja }}  
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
        { vrsta: 'vuk', ime: 'Ponos', datum_rodjenja: '05-06-2011'}
      ]
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
