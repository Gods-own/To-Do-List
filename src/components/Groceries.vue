<template>
    <div :key="grocery.id" v-for="grocery in groceries">
        <Grocery @delete-item="$emit('delete-item', $event)" :grocery="grocery" />
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
    emits: ['delete-item']
}
</script>