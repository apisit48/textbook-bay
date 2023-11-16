<script setup>
import { ref, onMounted } from 'vue'
import BookService from '@/services/BookService.js'

const theBook = ref(null)

const props = defineProps({
    id: { required: true }
})

onMounted(() => {
    BookService.getBook(props.id)
    .then((response)=>{
        theBook.value = response.data
    })
    .catch((error)=>{
        console.log(error)
    })
})
</script>

<template>
    <div v-if="theBook">
        <h1>{{  theBook.title }}</h1>
        <p>Type 1: {{ theBook.type1 }}  </p>
        <p>Type 2: {{ theBook.type2 }} </p>
        <p>Japanese Name: {{ theBook.jpname }}</p>
        <p>Evolution: {{ theBook.Evolution }} </p>
        <p>image_url: {{ theBook.image }} </p>
    </div>
</template>

<style scoped>
div {
  padding: 20px;
  margin: 20px auto;
  max-width: 600px; /* Adjust as per your layout */
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
}

/* Headings */
h1 {
  font-size: 1.8em;
  color: #333;
  margin-bottom: 10px;
}

/* Paragraphs */
p {
  font-size: 1em;
  line-height: 1.6;
  color: #666;
  margin-bottom: 8px;
}
</style>