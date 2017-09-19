<template>
    <div>
        <h3>Add Item</h3>
        <form @submit.prevent="addItem()">
            <div class="form-group">
                <label for="name">Item Name</label>
                <input type="text" id="name" name="name" class="form-control" v-model="item.name">
            </div>
            <div class="form-group">
                <label for="price">Item Price</label>
                <input type="text" id="price" name="price" class="form-control" v-model="item.price">
            </div>
            <div class="form-group">
                <button type="submit" class="btn btn-primary">Add Item</button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            item: {}
        }
    },
    methods: {
        addItem() {
            this.axios.post('/items', this.item).then((response) => {
                this.$router.push({ name: 'display-item' });
            });
        }
    }
}
</script>

<style>

</style>
