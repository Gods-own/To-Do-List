<template>
    <div class="container">
        <Header heading="Grocery Items" />
        <Groceries @delete-item="$emit('delete-item', $event)" :groceries="groceries" />
        <Button :onClick="onClear" title='Clear Items'/>
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
    methods: {
        onClear() {
            this.$emit('clear-items')
        }
    },
    emits: ['clear-items', 'delete-item']
}
</script>