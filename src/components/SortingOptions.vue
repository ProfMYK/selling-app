<template>
  <div
    class="rounded flex justify-between w-[1000px] items-center p-3 bg-gray-100"
  >
    <div class="flex gap-1">
      <label for="sort-by">Cube Type: </label>
      <select
        name="sort-by"
        id="sort-by"
        class="rounded"
        v-model="type"
        @change="changeType"
      >
        <option value="3x3">3x3</option>
        <option value="2x2">2x2</option>
      </select>
    </div>
    <div class="flex gap-3">
      <div class="flex gap-1">
        <label for="sort-by">Sort By:</label>
        <select
          name="sort-by"
          id="sort-by"
          class="rounded"
          v-model="sortBy"
          @change="sortItems"
        >
          <option value="price">Price</option>
          <option value="name">Name</option>
        </select>
      </div>
      <div class="flex gap-1">
        <label for="sort-order">Sort Order:</label>
        <select
          name="sort-order"
          id="sort-order"
          class="rounded"
          v-model="sortOrder"
          @change="sortItems"
        >
          <option value="asc">Ascending</option>
          <option value="desc">Descending</option>
        </select>
      </div>
    </div>
    <div class="flex gap-3">
      <input type="text" name="search" id="search" class="rounded" />
      <button
        class="rounded bg-gray-200 pl-2 pr-2 transition-all hover:bg-gray-300"
      >
        Search
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SortingOptions",
  data() {
    return {
      sortBy: "price",
      sortOrder: "asc",
      search: "",
      type: "3x3",
    };
  },
  methods: {
    sortItems() {
      this.$emit("sort-items", this.sortBy, this.sortOrder);
    },
    changeType() {
      this.$emit("change-type", this.type);
    },
  },
};
</script>
