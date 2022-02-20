<template>
  <div class="container">
    <AddGroceryBlock @add-grocery="addGrocery($event)" />
    <DisplayGroceryBlock @click-event="clearItems" @delete-grocery="deleteGrocery" :groceries="groceries" />
  </div> 
</template>

<script>
import AddGroceryBlock from './components/AddGroceryBlock'
import DisplayGroceryBlock from './components/DisplayGroceryBlock'

export default {
  name: 'App',
  components: {
    AddGroceryBlock,
    DisplayGroceryBlock
  },
  data() {
    return {
        groceries: []
    }
  },
  methods: {
    addGrocery(grocery) {
        this.groceries = [...this.groceries, grocery]
    },
    clearItems() {
      this.groceries = []
    },
    deleteGrocery(id) {
      this.groceries = this.groceries.filter((grocery) => grocery.id !== id)
    }
  }
}
</script>

<style>
.container {
  border: 1px solid black;
}
</style>


