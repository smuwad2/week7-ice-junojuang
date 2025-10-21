<script>
    export default { 
        // Add code in appropriate places
        data() {
            return {
                items: ['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'],
                newItem:"",
            }
            
        },
        methods:{
            removeItem(index){
                this.items.splice(index,1)
            },
            addItem(){
                this.items.push(this.newItem)
            }
        }
    }
</script>

<template>

    <h2>Shopping Cart</h2>
    <!-- TODO: Add Code Here -->
     <ul>
        <li v-for="(item, index) in items" :key="index">{{ item }}
            <button @click="removeItem(index)">Delete!</button></li>
     </ul>
     <input type="text" v-model="newItem"><button @click="addItem(newItem)">Add!</button></input>
     
   
</template>
