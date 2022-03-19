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
        const parsed = JSON.stringify(this.groceries);
        localStorage.setItem('groceries', parsed)
    },
    clearItems() {
      this.groceries = []
      const parsed = JSON.stringify(this.groceries);
      localStorage.setItem('groceries', parsed)
    },
    deleteGrocery(id) {
      this.groceries = this.groceries.filter((grocery) => grocery.id !== id)
      const parsed = JSON.stringify(this.groceries);
      localStorage.setItem('groceries', parsed)
    }, 
  },
  mounted() {
    if (localStorage.getItem('groceries')) {
        try {
            this.groceries = JSON.parse(localStorage.getItem('groceries'));
        } catch (e) {
            localStorage.removeItem('groceries');
        }
    }    
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
@media screen and (min-width: 385px) and (max-width: 538px){
	html {
		font-size: 19px;
	}
}
</style>


