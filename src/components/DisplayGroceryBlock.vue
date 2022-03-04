<template>
    <div class="seconddiv">
        <Message :class="{ active : isActive, clear : isCleared, removed : isRemoved }" :msg="msg" />
        <Header class="heading-second" heading="Grocery Items" />
        <Groceries @delete-item="updateMessage" :groceries="groceries" />
        <Button class="button second" :type="clearbtn" @click="onClear" title='Clear Items'/>
    </div>
</template>

<script>
import Message from './Message'
import Header from './Header'
import Button from './Button'
import Groceries from './Groceries'

export default {
    name: 'DisplayGroceryBlock',
    components: {
        Header,
        Button,
        Groceries,
        Message,
    },
    props: {
        groceries: Array
    },
    data() {
        return {
            clearbtn : 'button',
            msg : '',
            isActive: true,
            isCleared: true,
            isRemoved: true,
        }
    },
    methods: {
        onClear() {
            this.isCleared = false            
            this.msg = "No more items to Delete"
            this.isActive = false
            const showMessage = setTimeout(function () {
                this.isActive = true
                this.isCleared = true
            }.bind(this), 2000)               
            this.$emit('clearItems')
        },
        updateMessage(groceryId) {
            let grocery = this.groceries.filter((grocery) => grocery.id == groceryId)
            this.isRemoved = false             
            this.isActive = false
            this.msg = `${grocery[0].text} removed from items`            
            const showMessage = setTimeout(function () {
                this.isActive = true
                this.isRemoved = true                
            }.bind(this), 2000)                        
            this.$emit('deleteItem', groceryId)
        }
    },
    emits: ['clearItems', 'deleteItem']
}
</script>

<style scoped>
@import '../assets/styles/groceryblock.css';
.active {
    display: none;
}
</style>