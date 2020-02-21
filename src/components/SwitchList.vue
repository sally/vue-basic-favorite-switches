<template>
    <div id="switch-list">
        <div class="row">
            <div class="col-sm-12 col-md-9">
                <table class="striped">
                    <caption>la crème de la crème à la spark</caption>
                    <thead>
                        <tr>
                            <th>Name</th>
                            <th>Type</th>
                            <th>Bottom-Out</th>
                            <th>Modify</th>
                            <th>Delete</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="mechSwitch in switches" :key="mechSwitch.id">
                            <td data-label="Name" v-if="mechSwitch.id === idBeingEdited">
                                <input type="text"
                                    v-model="mechSwitch.name"
                                    v-bind:class="{ 'has-error': errors && invalidName(mechSwitch) }"
                                    @keypress="clearStatus"
                                    @focus="clearStatus"
                                />
                            </td>
                            <td data-label="Name" v-else>{{ mechSwitch.name }}</td>

                            <td data-label="Type" v-if="mechSwitch.id === idBeingEdited">
                                <input type="text"
                                    v-model="mechSwitch.type"
                                    v-bind:class="{ 'has-error': errors && invalidType(mechSwitch) }"
                                    @keypress="clearStatus"
                                    @focus="clearStatus"
                                />
                            </td>
                            <td data-label="Type" v-else>{{ mechSwitch.type }}</td>

                            <td data-label="Bottom-Out" v-if="mechSwitch.id === idBeingEdited">
                                <input type="text"
                                    v-model="mechSwitch.bottomOutForce"
                                    v-bind:class="{ 'has-error': errors && invalidType(mechSwitch) }"
                                    @keypress="clearStatus"
                                    @focus="clearStatus"
                                />
                            </td>
                            <td data-label="Bottom-Out" v-else>{{ mechSwitch.bottomOutForce }}</td>

                            <td data-label="Modify" v-if="mechSwitch.id === idBeingEdited">
                                <transition name="fade">
                                    <button v-if="errors" class="small secondary">
                                        Missing fields
                                    </button>
                                    <button v-else class="small tertiary" @click="validateSwitch(mechSwitch)">Update</button>
                                </transition>
                                <button class="small" @click="cancelUpdate(mechSwitch)">Cancel</button>
                                <br />
                            </td>
                            <td data-label="Modify" v-else>
                                <button class="small primary" @click="updateMode(mechSwitch)">Modify</button>
                            </td>

                            <td data-label="Delete">
                                <button class="small inverse" @click="deleteSwitch(mechSwitch.id)">Delete</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'switch-list',
    data() {
        return {
            idBeingEdited: null,
            errors: null,
        }
    },
    props: {
        switches: Array
    },
    methods: {
        cancelUpdate(mechSwitch) {
            Object.assign(mechSwitch, this.cachedSwitch);
            this.idBeingEdited = null;
        },
        deleteSwitch(id) {
            this.idBeingEdited = null;
            this.$emit('delete:switch', id);
        },
        updateMode(mechSwitch) {
            this.clearStatus();
            if (this.idBeingEdited) {
                this.switches.map(mechSwitch => {
                    mechSwitch.id === this.idBeingEdited ? Object.assign(mechSwitch, this.cachedSwitch) : mechSwitch;
                })
            }
            this.cachedSwitch = Object.assign({}, mechSwitch);
            this.idBeingEdited = mechSwitch.id;
        },
        validateSwitch(mechSwitch) {
            console.log(this.invalidName(mechSwitch));
            if (this.invalidName(mechSwitch) || this.invalidName(mechSwitch) || this.invalidBottomOut(mechSwitch)) {
                this.errors = true;
            } else {
                this.clearStatus();
            }

            if (!this.errors) {
                this.$emit('update:switch', mechSwitch);
            }
        },
        clearStatus() {
            this.errors = false;
        },
        invalidName(mechSwitch) {
            return !mechSwitch.name;
        },
        invalidType(mechSwitch) {
            return !mechSwitch.type;
        },
        invalidBottomOut(mechSwitch) {
            return !mechSwitch.bottomOutForce;
        },

    },
}
</script>

<style scoped>
    #switch-list table {
        max-height: none;
    }
</style>
