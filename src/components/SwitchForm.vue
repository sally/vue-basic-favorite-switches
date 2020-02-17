<template>
    <div id="switch-form">
        <div class="row">
            <div class="col-sm-12 col-md-6">
                <form @submit="$emit('add:switch', mechSwitch)">
                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="brand">Brand</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text" v-model="mechSwitch.brand" placeholder="e.g. 'Gateron'" />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="name">Name</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text" v-model="mechSwitch.name" placeholder="e.g. 'Brown'" />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="type">Type</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text" v-model="mechSwitch.type" placeholder="e.g. 'Tactile'" />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="bottomOutForce">Bottom-Out</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text" v-model="mechSwitch.bottomOutForce" placeholder="e.g. '60g'" />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-offset-4 col-md-4">
                            <input type="submit" class="button tertiary" value="Add Switch" />
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'switch-form',
    data() {
        return {
            mechSwitch: {
                brand: null,
                name: null,
                type: null,
                bottomOutForce: null,
            },
        }
    },
}
</script>

<style scoped />