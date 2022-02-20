<template>
    <div class="container">
        <Header heading="Grocery Items" />
        <Groceries @delete-grocery="$emit('delete-grocery', grocery.id)" :groceries="groceries" />
        <Button @click-event="$emit('click-event')" title='Clear Items'/>
    </div>
</template>

<script>
import Header from './Header'
import Button from './Button'
import Groceries from './Groceries'

export default {
    name: 'DisplayGroceryBlock',
    components: {
        Header,
        Button,
        Groceries
    },
    props: {
        groceries: Array
    },
    emits: ['click-event', 'delete-grocery']
}
</script>