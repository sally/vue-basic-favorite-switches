<template>
    <div id="switch-list">
        <table class="striped">
            <caption>la crème de la crème à la mini</caption>
            <thead>
                <tr>
                    <th>Brand</th>
                    <th>Name</th>
                    <th>Type</th>
                    <th>Bottom-Out</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="mechanicalSwitch in switches" :key="mechanicalSwitch.id">
                    <td data-label="Brand">{{ mechanicalSwitch.brand }}</td>
                    <td data-label="Name">{{ mechanicalSwitch.name }}</td>
                    <td data-label="Type">{{ mechanicalSwitch.type }}</td>
                    <td data-label="Bottom-Out Force">{{ mechanicalSwitch.bottomOutForce }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'switch-list',
    props: {
        switches: Array
    },
}
</script>

<style scoped>
    #switch-list table {
        max-height: none;
    }
</style>
