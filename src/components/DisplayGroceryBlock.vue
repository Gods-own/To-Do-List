<template>
    <div class="container">
        <Header heading="Grocery Items" />
        <Groceries @delete-item="$emit('deleteItem', $event)" :groceries="groceries" />
        <Button :type="clearbtn" @click="onClear" title='Clear Items'/>
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
    data() {
        return {
            clearbtn : 'button'
        }
    },
    methods: {
        onClear() {
            this.$emit('clearItems')
        }
    },
    emits: ['clearItems', 'deleteItem']
}
</script>