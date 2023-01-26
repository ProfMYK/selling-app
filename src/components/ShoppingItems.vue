<template>
  <div class="w-[1000px] pt-3 grid grid-cols-5 gap-3">
    <ShoppingItem
      v-for="item in this.items"
      :key="item.id"
      :name="item.name"
      :price="item.price"
      :image="item.image"
      :color="item.color"
    />
  </div>
</template>

<script>
import ShoppingItem from "@/components/ShoppingItem";

export default {
  name: "ShoppingItems",
  components: {
    ShoppingItem,
  },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>
