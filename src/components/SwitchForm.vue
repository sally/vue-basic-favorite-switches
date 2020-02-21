<template>
    <div id="switch-form">
        <div class="row">
            <div class="col-sm-12 col-md-6">
                <form @submit.prevent="validateSwitch">
                    <div class="row">
                        <div class="col-sm-12 col-md-4">
                            <label for="name">Name</label>
                        </div>
                        <div class="col-sm-12 col-md-8">
                            <input type="text"
                                v-model="mechSwitch.name"
                                placeholder="e.g. 'Brown'"
                                v-bind:class="{ 'has-error': errors && invalidName }"
                                @keypress="clearStatus"
                                @focus="clearStatus"
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
                                @keypress="clearStatus"
                                @focus="clearStatus"
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
                                @keypress="clearStatus"
                                @focus="clearStatus"
                            />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-offset-4 col-md-4">
                            <input type="submit" class="button primary" value="Add Switch" />
                        </div>
                    </div>

                    <div class="row">
                        <div class="col-sm-12 col-md-offset-4 col-md-4">
                            <transition name="fade">
                                <mark v-if="errors" class="secondary switch-form-error">
                                    <span class="icon-alert inverse"></span>
                                    Missing fields
                                </mark>
                                <mark v-if="success" class="tertiary switch-form-error">
                                    <span class="icon-info inverse"></span>
                                    Successfully added
                                </mark>
                            </transition>
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
                name: null,
                type: null,
                bottomOutForce: null,
            },
        }
    },
    computed: {
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
        clearStatus() {
            this.errors = false;
            this.success = false;
        },
        validateSwitch() {
            if (this.invalidName || this.invalidType || this.invalidBottomOut) {
                this.errors = true;
            } else {
                this.clearStatus();
            }

            if (!this.errors) {
                this.$emit('add:switch', this.mechSwitch);
                for (const property in this.mechSwitch) {
                    this.mechSwitch[property] = null;
                }

                this.success = true;
                setTimeout(() => {
                    this.clearStatus();
                }, 5000);
            }
        }
    }
}
</script>

<style scoped />