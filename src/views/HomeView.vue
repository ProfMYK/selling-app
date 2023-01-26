<template>
  <div class="w-full flex justify-center items-center p-3 gap-3 h-max">
    <!-- Sorting Options -->
    <div class="bg-gray-100 p-3 flex flex-col w-96 text-left">
      <!-- Searching options -->
      <p>jhudfsugh iudshfuighdfg</p>
      <h1>ijiadsjfj aoisdjifj sd</h1>
      <h2>idjfg jdfjgi djifjghidf jgij</h2>
    </div>
    <div class="">
      <SortingOptions @sort-items="sortItems" @change-type="changeType" />
      <ShoppingItems :items="items" />
    </div>
  </div>
</template>

<script>
import SortingOptions from "@/components/SortingOptions";
import ShoppingItems from "@/components/ShoppingItems";

export default {
  name: "HomeView",
  components: {
    SortingOptions,
    ShoppingItems,
  },
  data() {
    return {
      items: [],
      type: "3x3",
    };
  },
  async created() {
    await this.fetchItems(this.type);
    this.sortItems("price", "asc");
  },
  methods: {
    async fetchItems(type) {
      const res = await fetch(`http://localhost:3000/${type}`);
      const data = await res.json();

      this.items = data;
    },
    sortItems(by, order) {
      if (by === "price") {
        if (order === "asc") {
          this.items.sort((a, b) => a.price - b.price);
        } else {
          this.items.sort((a, b) => b.price - a.price);
        }
      } else {
        if (order === "asc") {
          this.items.sort((a, b) => a.name.localeCompare(b.name));
        } else {
          this.items.sort((a, b) => b.name.localeCompare(a.name));
        }
      }
      console.log(this.items);
    },
    changeType(type) {
      this.type = type;
      this.fetchItems(type);
    },
  },
};
</script>
