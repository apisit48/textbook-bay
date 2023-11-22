<script setup>
import { ref, onMounted } from 'vue'
import { db } from '@/js/firebase.js'
import { collection, onSnapshot } from "firebase/firestore";

import ProductCard from '@/components/ProductCard.vue'

const pokedex = ref([])

async function getBooks() {


  onSnapshot(collection(db, 'pokedex'), (querySnapshot) => {
    let pokedexSnapshot = []
    querySnapshot.forEach((doc) => {
      let pokemon = {
        "id": doc.id,
        "title": doc.data().title,
        "type1": doc.data().type1,
        "type2": doc.data().type2,
        "jpname": doc.data().jpname,
        "Evolution": doc.data().Evolution,
        "image": doc.data().image
      }

      pokedexSnapshot.push(pokemon)
    })
    pokedex.value = pokedexSnapshot
  })
}

onMounted(async () => {
    console.log("Connecting to Firebase")
    await getBooks()
})


</script>

<template>
  <div class="products">
    <ProductCard v-for="book in pokedex" :key="book.id" :book="book" />
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}

.products {
  display: flex;
  flex-wrap: wrap;
  width: 600px;
  margin-bottom: 10px;
  margin-left: 460px;
  justify-content: center;
  background-color: aqua;
  border: 3px solid #39495c;
}
</style>
