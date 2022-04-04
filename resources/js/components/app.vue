<template>
    <div class="w-[350px] m-auto">
        <div class="p-2 bg-[#e6e6e6]">
            <h2 id="title" class="text-3xl text-center">Todo List</h2>
            <add-item-form
                v-on:reloadlist="getItems()"
             />
        </div>
        <list-view
            :items="items"
            v-on:reloadlist="getItems()"
        />
    </div>
</template>

<script>
import addItemForm from './addItemForm.vue'
import listView from './listView.vue'

export default {
    components: { addItemForm, listView },
    data: () => {
        return {
            items: []
        }
    },
    methods: {
        getItems(){
            axios.get('api/items')
            .then(response => {
                this.items = response.data
            })
            .catch(error => {
                console.log(error)
            })
        }
    },
    created(){
        this.getItems()
    }
}
</script>