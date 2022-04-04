<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item 
                :item="item"
                class="bg-[#e6e6e6] p-1 mt-1"
                v-on:itemchanged="$emit('reloadlist')" />
        </div>
    </div>
</template>

<script>
import listItem from './listItem.vue'

export default {
    props: ['items'],
    components: { listItem }
}
</script>