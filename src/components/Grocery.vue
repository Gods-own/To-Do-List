<template>
    <div class="grocery">
        <div><p>{{grocery.text}}</p></div>
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
    font-size: 1.2rem;
}

p {
    font-size: 1rem;
    text-transform: capitalize;
    margin-top: 0.6rem;
    margin-bottom: 0.6rem;
}
.grocery {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    align-items: center;
    background-color: #f4efef;
    margin-top: 1rem;
    padding-left: 0.7rem;
    padding-right: 0.6rem;
}

.grocery div {
    max-width: 80%;
    word-wrap: break-word;
}

@media screen and (min-width: 539px) {
    .delete-btn {
        font-size: 1.4rem;
    }
    p {
        font-size: 20px;
        margin-top: 0.6rem;
        margin-bottom: 0.6rem;
    } 
}
</style>