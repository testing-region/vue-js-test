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
        }
    },

    methods: {
        addItem(item) {
            this.items.push({
                id: this.items.length + 1,
                label: item
            })
            this.newItem = ""
        }
    },
}
</script>

<template>
    <h1>{{ header }}</h1>
    <input type="text" v-model.lazy="newItem" placeholder="Enter an item" />
    <button type="button" class="add-item" v-on:click="addItem(newItem)">Add item</button>
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
