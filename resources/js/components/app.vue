<template>
    <div class="w-[350px] m-auto"> <!-- todoListContainer -->
        <div class="p-2 bg-[#e6e6e6]"> <!-- heading -->
            <h2 id="title" class="text-3xl text-center">Todo List</h2>
            <add-item-form />
        </div>
        <list-view />
    </div>
</template>

<script>
import addItemForm from './addItemForm.vue'
import listView from './listView.vue'

export default {
    components: {
        addItemForm,
        listView
    }
}
</script>

AddItemForm