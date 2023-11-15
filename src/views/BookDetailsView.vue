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
        <p>Type: {{ theBook.price }} Abilities: {{ theBook.condition }} </p>
        <p>Catch rate: {{ theBook.isbn }} Hatch time: {{ theBook.published }}</p>
    </div>
</template>