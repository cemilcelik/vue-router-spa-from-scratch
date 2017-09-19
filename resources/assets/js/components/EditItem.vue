<template>
    <div>
        <h3>Update Item</h3>
        <form @submit.prevent="updateItem">
            <div class="form-group">
                <label for="name">Item Name</label>
                <input type="text" id="name" class="form-control" v-model="item.name">
            </div>
            <div class="form-group">
                <label for="price">Item Price</label>
                <input type="text" id="price" class="form-control" v-model="item.price">
            </div>
            <div class="form-group">
                <button class="btn btn-primary">Update Item</button>
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
    created: function() {
        this.fetchItem();
    },
    methods: {
        fetchItem() {
            this.axios.get('/items/' + this.$route.params.id + '/edit').then((response) => {
                this.item = response.data;
            });
        },
        updateItem() {
            this.axios.put('/items/' + this.$route.params.id, this.item).then((response) => {
                this.$router.push({ name: 'display-item' });
            }).catch((error) => {
                if (error.response.data.errors) {
                    alert(error.response.data.message);
                }
            });
        }
    }
}
</script>

<style>

</style>
