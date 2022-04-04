<template>
    <div class="flex justify-center items-center"> <!-- addItem -->
        <input v-model="item.name" type="text" class="bg-[#f7f7f7] border-none outline-none p-1 mr-2 w-full" />
        <font-awesome-icon
            icon='plus-square'
            class="text-xl"
            @click="addItem()"
            :class="[ item.name ? 'text-[#00ce25]' : 'text-[#999999]' ]"/>
    </div>
</template>

<script>
export default {
    data: function(){
        return {
            item: {
                name: ''
            }
        }
    },
    methods: {
        addItem(){
            if(this.item.name == '') return

            axios.post('api/items', {
                name: this.item.name
            })
            .then(response => {
                if(response.status == 201){
                    this.item.name == ''
                }
            })
            .catch(error => {
                console.log(error)
            })
        }
    }
}
</script>