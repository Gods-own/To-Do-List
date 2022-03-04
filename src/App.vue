<template>
  <div>
    <AddGroceryBlock @add-grocery="addGrocery" />
    <DisplayGroceryBlock @clear-items="clearItems" @delete-item="deleteGrocery" :groceries="groceries" />
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
    }, 
  }
}
</script>

<style>
*{
	box-sizing: border-box;
}
body{
	background-color: brown;
}
.container {
  border: 1px solid black;
}
</style>


