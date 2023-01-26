<template>
  <button
    class="rounded text-sm p-3 flex flex-col justify-between gap-2 bg-gray-100 transition-all hover:bg-gray-200"
  >
    <div class="w-full text-left flex flex-col gap-2">
      <img :src="image" alt="" />
      <h1>{{ name }} - {{ color }}</h1>
    </div>
    <div class="w-full text-left flex flex-col gap-2">
      <p class="font-bold">${{ price }}</p>
      <button class="p-1.5 w-[96%] bg-green-600 rounded">Add To Cart</button>
    </div>
  </button>
</template>

<script>
export default {
  name: "ShoppingItem",
  props: {
    name: String,
    price: Number,
    image: String,
    color: String,
  },
};
</script>
