<template>
    <form  @submit.prevent="submitGrocery">
        <div>
            <input class="input" type="text" v-model="text" name="grocery">
        </div>
        <div>
            <Button class="button first">Submit Here</Button>
        </div>
    </form>
</template>

<script>
import Button from './Button'
export default {
    name: 'AddGrocery',
    components: {
        Button
    },
    data() {
        return {
            text: '',
            groceryItems: []
        }
    },
    methods: {
        submitGrocery() {
            let newGrocery
            if(!this.text) {
                newGrocery = null
            } else {

                let id;
                let uniqueId;
                let index;

                do {
                    uniqueId = Math.floor(Math.random() * 10000)
                    index = this.groceryItems.findIndex((groceryItem) => {
                    return groceryItem.id === uniqueId
                    })
                } 
                while(index !== -1)

                id = uniqueId

                newGrocery = {
                    id: id,
                    text: this.text
                }
            }  
            this.text = ''
            this.$emit('addGrocery', newGrocery)
        } 
    },
    emits: ['addGrocery'],
    mounted() {
        if (localStorage.getItem('groceries')) {
            try {
                this.groceryItems = JSON.parse(localStorage.getItem('groceries'));
            } catch (e) {
                localStorage.removeItem('groceries');
            }
        }    
     }
}
</script>

<style scoped>
.input {
    border-style: none none solid none;
    outline: none;
    width: 93%;
    font-size: 1rem;
}
@media screen and (min-width: 539px) {
    .input {
        width: 350px;
        font-size: 20px;
    }
}
</style>