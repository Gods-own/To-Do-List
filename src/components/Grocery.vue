<template>
    <div>
        <p>{{grocery.text}}</p>
        <Button class="delete-btn" :type="deletebtn" @click="onDelete(grocery.id)" title="X" />
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

<style scoped>
.delete-btn {
    border: none;
    outline: none;
    width: 30px;
    height: 30px;
    border-radius: 15px;
    background-color: black;
    color: white;
    float: right;
}
div {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
p {
    font-size: 20px;
    text-transform: capitalize;
}
</style>