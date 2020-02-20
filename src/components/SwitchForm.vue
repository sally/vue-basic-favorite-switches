<template>
    <div id="switch-form">
        <div class="row">
            <div class="col-sm-12 col-md-6">
                <form @submit.prevent="validateSwitch">
                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="brand">Brand</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text"
                                v-model="mechSwitch.brand"
                                placeholder="e.g. 'Gateron'"
                                v-bind:class="{ 'has-error': errors && invalidBrand }"
                            />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="name">Name</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text"
                                v-model="mechSwitch.name"
                                placeholder="e.g. 'Brown'"
                                v-bind:class="{ 'has-error': errors && invalidName }"
                            />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="type">Type</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text"
                                v-model="mechSwitch.type"
                                placeholder="e.g. 'Tactile'"
                                v-bind:class="{ 'has-error': errors && invalidType }"
                            />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="bottomOutForce">Bottom-Out</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text"
                                v-model="mechSwitch.bottomOutForce"
                                placeholder="e.g. '60g'"
                                v-bind:class="{ 'has-error': errors && invalidBottomOut }"
                            />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-offset-4 col-md-4">
                            <input type="submit" class="button tertiary" value="Add Switch" />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-offset-4 col-md-4">
                            <mark v-if="errors" class="secondary switch-form-error">
                                <span class="icon-alert inverse"></span>
                                Missing fields
                            </mark>
                            <mark v-if="success" class="tertiary switch-form-error">
                                <span class="icon-info inverse"></span>
                                Successfully added
                            </mark>
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
            errors: false,
            success: false,
            mechSwitch: {
                brand: null,
                name: null,
                type: null,
                bottomOutForce: null,
            },
        }
    },
    computed: {
        invalidBrand() {
            return !this.mechSwitch.brand;
        },
        invalidName() {
            return !this.mechSwitch.name;
        },
        invalidType() {
            return !this.mechSwitch.type;
        },
        invalidBottomOut() {
            return !this.mechSwitch.bottomOutForce;
        },
    },
    methods: {
        validateSwitch() {
            if (this.invalidBrand || this.invalidName || this.invalidType || this.invalidBottomOut) {
                this.errors = true;
            } else {
                this.errors = false;
            }

            if (!this.errors) {
                this.$emit('add:switch', this.mechSwitch);
                this.success = true;

                setTimeout(() => {
                    this.success = false;
                }, 5000);
            }
        }
    }
}
</script>

<style scoped>
    .switch-form-error {
        margin: 8px;
    }

    .has-error {
        border: 1px solid #d92121;
    }
</style>