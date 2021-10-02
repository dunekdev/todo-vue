<template>
    <div class="item" :class="{completed: item.completed}">
    <h2>{{ item.title }}</h2>
    <button v-if="!item.completed" @click="completeItem()">Ukończone</button><button @click="removeItem()">Usuń</button>
    </div>
</template>

<script>
export default {
    props: ['item'],
    methods: {
        completeItem(){
            this.$emit('removeClicked', this.item.id)
        },
        removeItem(){
            this.$emit('deleteClicked', this.item.id)
        }
    }
}
</script>
