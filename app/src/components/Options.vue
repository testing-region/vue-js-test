<script>
export default {
    data() {
        return {
            header: "Shopping List App",
            newItem: "",
            items: [
                { id: 1, label: "Orange", purchased: true },
                { id: 2, label: "Mangoes", purchased: true },
                { id: 3, label: "Tomatoes", purchased: false },
                { id: 4, label: "Ice Cream", purchased: false },
            ],
            editing: false,
        }
    },

    methods: {
        addItem() {
            this.items.push({
                id: this.items.length + 1,
                label: this.newItem
            })
            this.newItem = ""
        },

        doEdit(editing) {
            this.editing = editing
            this.newItem = ""
        },

        togglePurchased(item) {
            item.purchased = !item.purchased
        }
    },
}
</script>

<template>
    <div class="header">
        <h1>{{ header }}</h1>
        <button v-if="editing" @click="doEdit(false)" class="no-edit">
            Cancel
        </button>
        <button v-else @click="doEdit(true)" class="edit">
            Add Item
        </button>
    </div>

    <div v-if="editing">
        <input type="text" v-model="newItem" placeholder="Enter an item" />
        <button :disabled="newItem.length === 0" type="button" class="add-item" @click="addItem">
            Add item
        </button>
    </div>

    <p v-if="items.length === 0">Nice job! You bought all the items</p>

    <ul class="shopping-list">
        <li v-for="item in items" @click="togglePurchased(item)" :class="{ strikeout: item.purchased }" :key="item.id">
            {{ item.label }}
        </li>
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

.no-edit {
    background-color: red;
    margin: 8px;
}

.edit {
    background-color: green;
    margin: 8px;
}

.strikeout {
    text-decoration-line: line-through;
}
</style>
