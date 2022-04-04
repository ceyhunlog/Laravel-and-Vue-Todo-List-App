<template>
    <div class="flex justify-center items-center">
        <input
            type="checkbox"
            @change="updateCheck()"
            v-model="item.completed"
        />

        <span
            :class="item.completed ? 'line-through text-[#999999]' : ''"
            class="w-full ml-5">
            {{item.name}}
        </span>

        <button
            @click="removeItem()"
            class="bg-[#e6e6e6] text-[#ff0000] border-none outline-none">
            <font-awesome-icon icon='trash' />
        </button>
    </div>
</template>

<script>
export default {
    props: ['item'],
    methods: {
        updateCheck(){
            axios.put('api/items/' + this.item.id, {
                completed: this.item.completed
            })
            .then(response => {
                if(response.status == 200){
                    this.$emit('itemchanged')
                }
            })
            .catch(error => {
                console.log(error)
            })
        },
        removeItem(){
            axios.delete('api/items/' + this.item.id)
            .then(response => {
                if(response.status == 200){
                    this.$emit('itemchanged')
                }
            })
            .catch(error => {
                console.log(error)
            })
        }
    }
}
</script>