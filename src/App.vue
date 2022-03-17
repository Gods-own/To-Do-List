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
@import "https://maxst.icons8.com/vue-static/landings/line-awesome/line-awesome/1.3.0/css/line-awesome.min.css";
*{
	box-sizing: border-box;
}
body{
	background: linear-gradient(to right, #3B8BEA, #F070A1)
}
</style>


