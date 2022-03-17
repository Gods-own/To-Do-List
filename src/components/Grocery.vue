<template>
    <div class="grocery">
        <p>{{grocery.text}}</p>
        <Button class="delete-btn" :type="deletebtn" @click="onDelete(grocery.id)"><i class="las la-trash"></i></Button>
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
    background-color: transparent;
    color: black;
    font-size: 1.4rem;
}
div {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
p {
    font-size: 20px;
    text-transform: capitalize;
    margin-top: 0.6rem;
    margin-bottom: 0.6rem;
}
.grocery {
    background-color: #f4efef;
    margin-top: 1rem;
    padding-left: 0.7rem;
    padding-right: 0.6rem;
    border-radius: 5px;
}
</style>