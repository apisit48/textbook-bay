<script setup>

defineProps({
  book: {
    type: Object,
    required: true,
  }
})

</script>

<template>
  <div class="product-container">

  <!-- <RouterLink to="book/100001"> -->
  <RouterLink :to="{ name: 'book-details', params: {id: book.id} }" >
    <div class="product-card">
      <img :src="book.image" alt="Book Image" />
      <h2>{{ book.title }}</h2>
    </div>
  
  </RouterLink>
</div>
</template>

<style scoped>
.product-container {
  display: flex;
  flex-wrap: wrap; /* Allow items to wrap to the next line */
  justify-content: center; /* Center items horizontally */
  gap: 10px; /* Space between the cards */
}
.product-card {
  padding: 10px; /* Reduced padding */
  width: 200px; /* Set a specific width */
  max-height: 300px; /* Set a maximum height */
  box-sizing: border-box; /* Include padding and border in the width and height */
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
  display: flex;
  flex-direction: column;
  align-items: center; /* Center content horizontally */
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