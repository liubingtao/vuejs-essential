<template>
    <div v-show="show" :class="`alert alert-${type} alert-dismissible`">
        <button @click="clone" type="button" class="clone"><span>x</span></button>
        {{msg}}
    </div>
</template>

<script>
    export default {
        name: "Message",
        props: {
            show: {
                type: Boolean,
                default: false
            },
            type: {
                type: String,
                default: 'success'
            },
            msg: {
                type: String,
                default: ''
            }
        },
        watch: {
            show(value) {
                if (value) {
                    this.$nextTick(() => {
                        this.$el.scrollIntoView(true)
                    })
                }
            }
        },
        methods: {
            clone() {
                this.$emit('update:show', false)
            }
        }
    }
</script>

<style scoped>

</style>