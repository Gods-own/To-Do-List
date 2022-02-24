<template>
    <div>
        <p>{{grocery.text}}</p>
        <Button :onClick="onDelete(grocery.id)" title='X'/>
    </div>
</template>

<script>
import Button from './Button'

export default {
    name: "Grocery",
    props: {
        grocery: Object
    },
    components: {
        Button
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-item', id)
        }
    },
    emits: ['delete-item']
}
</script>