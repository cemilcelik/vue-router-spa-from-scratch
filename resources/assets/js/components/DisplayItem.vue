<template>
    <div>
        <div class="row">
            <div class="col-xs-10"></div>
            <div class="col-xs-2">
                <router-link :to="{ name: 'create-item' }" class="btn btn-primary btn-block">Create Item</router-link>
            </div>
        </div>
        <h3>List</h3>
        <table class="table table-hover">
            <thead>
                <tr>
                    <td>Id</td>
                    <td>Name</td>
                    <td>Price</td>
                    <td width="150">Process</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in items">
                    <td>{{ item.id }}</td>
                    <td>{{ item.name }}</td>
                    <td>{{ item.price }}</td>
                    <td>
                        <router-link :to="{ name: 'edit-item', params: { id: item.id } }" class="btn btn-warning">Edit</router-link>
                        <a href="#" class="btn btn-danger" @click="deleteItem(item.id, index)">Delete</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            items: []
        }
    },
    created() {
        this.fetchItems();
    },
    methods: {
        fetchItems() {
            this.axios.get('/items').then((response) => {
                this.items = response.data;
            });
        },
        deleteItem(id, index) {
            this.axios.delete('/items/' + id).then((response) => {
                this.items.splice(index, 1);
            });
        }
    }
}
</script>

<style>

</style>
