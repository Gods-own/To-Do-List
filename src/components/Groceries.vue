<template>
    <div :key="grocery.id" v-for="grocery in groceries">
        <Grocery :grocery="grocery"  @delete-item="$emit('deleteItem', grocery.id)" />
    </div>
</template>

<script>
import Grocery from './Grocery'
export default {
    name: "Groceries",
    props: {
        groceries: Array
    },
    components: {
        Grocery
    },
    emits: ['deleteItem']
}
</script>