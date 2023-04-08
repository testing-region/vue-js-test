<script>
export default {
    data() {
        return {
            header: "Shopping List App",
            newItem: "",
            items: [
                { id: 1, label: "Orange" },
                { id: 2, label: "Mangoes" },
                { id: 3, label: "Tomatoes" },
                { id: 4, label: "Ice Cream" },
            ],
            count: 0
        }
    },

    methods: {
        addItem(item) {
            this.items.push({
                id: this.count,
                label: item
            })
            this.count++
            this.newItem = ""
        }
    },

    mounted() {
        this.count = this.items.length
    },
}
</script>

<template>
    <h1>{{ header }}</h1>
    <input type="text" v-model.lazy="newItem" placeholder="Enter an item" />
    <button type="button" class="add-item" @click="addItem(newItem)">Add item</button>
    <ul class="shopping-list">
        <li v-for="item in items" :key="item.id">{{ item.label }}</li>
    </ul>
</template>

<style scoped>
.shopping-list {
    list-style-type: none;
    padding: 0;
}

.add-item {
    margin-left: 5px;
}
</style>
