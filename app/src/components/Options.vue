<script>
export default {
    data() {
        return {
            header: "Shopping List App",
            items: [
                { id: 1, label: "Orange" },
                { id: 2, label: "Mangoes" },
                { id: 3, label: "Tomatoes" },
                { id: 4, label: "Ice Cream" },
            ]
        }
    },
}
</script>

<template>
    <h1>{{ header }}</h1>
    <ul class="shopping-list">
        <li v-for="item in items" :key="item.id">{{ item.label }}</li>
    </ul>
</template>

<style scoped>
.shopping-list {
    list-style-type: none;
}
</style>
