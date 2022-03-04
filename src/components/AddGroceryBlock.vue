<template>
    <div class="container">
        <Header heading="Add Grocery Items" />
        <AddGrocery @add-grocery="$emit('addGrocery', $event)" />
    </div> 
</template>

<script>
import Header from './Header'
import AddGrocery from './AddGrocery'

export default {
    name: 'AddGroceryBlock',
    components: {
        Header,
        AddGrocery
    },
    emits: ['addGrocery']
}
</script>