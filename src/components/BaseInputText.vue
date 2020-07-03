<template>
    <input type="text" class="input" :value="value" v-on="listeners" />
</template>

<script>
    export default {
        name: 'BaseInputText',
        props: {
            value: {
                type: String,
                default: ""
            }
        },
        computed: {
            listeners () {
                    return {
                        ...this.$listeners,
                        input: event => this.$emit("input", event.target.value)
                    }
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

    $vue-blue: #32485F;

    .input {
        width: 100%;
        padding: 8px 10px;
        border: 1px solid $vue-blue;
    }
</style>
