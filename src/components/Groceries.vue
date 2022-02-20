<template>
    <div :key="grocery.id" v-for="grocery in groceries">
        <Grocery @delete-grocery="$emit('delete-grocery', grocery.id)" :grocery="grocery" />
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
    emits: ['delete-grocery']
}
</script>