<template>
    <div class="firstdiv">
        <Message class="add" :class="{ active : isActive }" :msg="msg" />
        <Header class=".heading-first" heading="Add Grocery Items" />
        <AddGrocery @add-grocery="updateMessage" />
    </div> 
</template>

<script>
import Message from './Message'
import Header from './Header'
import AddGrocery from './AddGrocery'
export default {
    name: 'AddGroceryBlock',
    components: {
        Header,
        AddGrocery,
        Message,
    },
    data() {
        return {
            msg : '',
            isActive: true,
        }
    },
    methods: {
        updateMessage(grocery) {
            this.msg = `${grocery.text} added to items` 
            this.isActive = false
            const showMessage = setTimeout(function () {
                this.isActive = true
            }.bind(this), 2000)
            this.$emit('addGrocery', grocery)
        }
    },
    emits: ['addGrocery']
}
</script>

<style scoped>
@import '../assets/styles/groceryblock.css';
.active {
    display: none;
}
</style>