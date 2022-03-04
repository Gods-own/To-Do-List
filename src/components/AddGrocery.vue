<template>
    <form  @submit.prevent="submitGrocery">
        <div>
            <input class="input" type="text" v-model="text" name="grocery">
        </div>
        <div>
            <Button class="button first" title="Submit Here" />
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
            text: ''
        }
    },
    methods: {
        submitGrocery() {
            if(!this.text) {
                alert('Please add an item')
                return
            }
            const newGrocery = {
                id: Math.floor(Math.random() * 10000),
                text: this.text
            }
            this.text = ''
            this.$emit('addGrocery', newGrocery)
        } 
    },
    emits: ['addGrocery']
}
</script>

<style scoped>
.input {
    border: 2px solid skyblue;
    border-style: none none solid none;
    background-color: darkred;
    outline: none;
    width: 350px;
    color: skyblue;
    font-size: 20px;
}
</style>