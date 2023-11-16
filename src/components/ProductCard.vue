<script setup>

defineProps({
  book: {
    type: Object,
    required: true,
  }

  
})

</script>

<template>
  <RouterLink :to="{ name: 'book-details', params: { id: book.id } }">
    <div class="product-card">
      <img :src="book.image" alt="Book Image" />
      <h2>{{ book.title }}</h2>
    </div>
  </RouterLink>
</template>

<style scoped>

.product-card {
  padding: 10px; 
  width:200px; 
  max-height: 200px; 
  box-sizing: border-box; 
  cursor: pointer;
  border: 1px solid #39495c;
  margin-top:  18px;
  margin-bottom: 18px;
  display: flex;
  flex-direction: column;
  align-items: center; 
}

.product-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}
.product-card img {
  max-width: 100px; 
  max-height: 100px; 
}
</style>