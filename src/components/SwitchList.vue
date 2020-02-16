<template>
    <div id="switch-list">
        <table class="striped">
            <caption>la crème de la crème à la spark</caption>
            <thead>
                <tr>
                    <th>Brand</th>
                    <th>Name</th>
                    <th>Type</th>
                    <th>Bottom-Out</th>
                    <th>Modify</th>
                    <th>Delete</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="mechanicalSwitch in switches" :key="mechanicalSwitch.id">
                    <td data-label="Brand" v-if="mechanicalSwitch.id === idBeingEdited">
                        <input type="text" v-model="mechanicalSwitch.brand" />
                    </td>
                    <td data-label="Brand" v-else>{{ mechanicalSwitch.brand }}</td>

                    <td data-label="Name" v-if="mechanicalSwitch.id === idBeingEdited">
                        <input type="text" v-model="mechanicalSwitch.name" />
                    </td>
                    <td data-label="Name" v-else>{{ mechanicalSwitch.name }}</td>

                    <td data-label="Type" v-if="mechanicalSwitch.id === idBeingEdited">
                        <input type="text" v-model="mechanicalSwitch.type" />
                    </td>
                    <td data-label="Type" v-else>{{ mechanicalSwitch.type }}</td>

                    <td data-label="Bottom-Out" v-if="mechanicalSwitch.id === idBeingEdited">
                        <input type="text" v-model="mechanicalSwitch.bottomOutForce" />
                    </td>
                    <td data-label="Bottom-Out" v-else>{{ mechanicalSwitch.bottomOutForce }}</td>

                    <td data-label="Modify" v-if="mechanicalSwitch.id === idBeingEdited">
                        <button class="small tertiary" @click="updateSwitch(mechanicalSwitch)">Update</button>
                        <button class="small secondary" @click="cancelUpdate">Cancel</button>
                    </td>
                    <td data-label="Modify" v-else>
                        <button class="small primary" @click="updateMode(mechanicalSwitch.id)">Modify</button>
                    </td>

                    <td data-label="Delete">
                        <button class="small inverse" @click="deleteSwitch(id)">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'switch-list',
    data() {
        return {
            idBeingEdited: null,
        }
    },
    props: {
        switches: Array
    },
    methods: {
        cancelUpdate() {
            this.idBeingEdited = null;
        },
        deleteSwitch(id) {
            this.idBeingEdited = null;
            this.$emit('delete:switch', id);
        },
        updateMode(id) {
            this.idBeingEdited = id;
        },
        updateSwitch(mechanicalSwitch) {
            this.idBeingEdited = null;
            this.$emit('update:switch', mechanicalSwitch);
        },
    },
}
</script>

<style scoped>
    #switch-list table {
        max-height: none;
    }
</style>
