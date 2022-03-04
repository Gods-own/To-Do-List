<template>
  <div class="container">
    <AddGroceryBlock @addgrocery="addGrocery" />
    <DisplayGroceryBlock @delete-item="deleteGrocery" @clear-items="clearItems" :groceries="groceries" />
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
      console.log('meca')
      this.groceries = []
    },
    deleteGrocery(id) {
      
      console.log(id)
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


