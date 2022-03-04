<template>
    <div>
        <p>{{grocery.text}}</p>
        <Button :type="deletebtn" @click.stop="onDelete(grocery.id)" title="X" />
    </div>
</template>

<script>
import Button from './Button'

export default {
    name: "Grocery",
    props: {
        grocery: Object
    },
    data() {
        return {
            deletebtn : 'button'
        }
    },
    components: {
        Button
    },
    methods: {
        onDelete(id) {
            console.log('finger')
            this.$emit('deleteItem', id)
        }
    },
    emits: ['deleteItem'],
}
</script>