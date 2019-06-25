<template>
<div>
    <form @submit.prevent="addAnimal"> 
      <div>
        <label for="vrsta">Vrsta : </label>
        <input type="text" id="vrsta" v-model="newAnimal.vrsta" required/>
      </div>
      <div>
        <label for="ime">Ime : </label>
        <input type="text" id="ime" v-model="newAnimal.ime" required/>
      </div>
      <div>
        <label for="datum_rodjenja">Datum rodjenja : </label>
        <input type="date" id="datum_rodjenja" v-model="newAnimal.datum_rodjenja" required/>
      </div>
      <div>
        <button type="submit">Add animal</button>
      </div>
    </form>
    <ul>
      <li v-for="(animal,index) in animals" :key="index">
        Vrsta : {{ animal.vrsta }} , ime : {{ animal.ime}} , datum rodjenja : {{ animal.datum_rodjenja ? animal.datum_rodjenja : 'Nepoznat' }}
        <button @click="removeAnimal(index)"> Remove </button>
        <button @click="moveToTop(index)"> Move to top </button>
      </li>
    </ul>
    </div>
</template>

<script>
export default {
  name: 'AnimalList',
  props: {
    msg: String
  },

  data (){
    return {
      newAnimal: this.getDefault(),

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
    },

    addAnimal(){
      this.animals.push({...this.newAnimal})
      this.newAnimal = this.getDefault()
    },

    getDefault () {
      return {
        vrsta: '',
        ime: '',
        datum_rodjenja: ''
      }
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
