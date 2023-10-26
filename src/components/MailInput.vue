<template>
    <label
        >Please enter the e-mail:
        <input ref="inp" type="text" v-model="mailVal" />
    </label>
    <button v-if="isVisible" type="button" @click="clearInput">Clear Input</button>
</template>
<script>
import { data } from '../constans/data.js'
export default {
    name: 'MailInput',

    props: {
        mail: {
            type: String,
        },
        mailModifiers: { default: () => ({}) },
    },

    data() {
        return {
            isVisible: false,
        }
    },

    computed: {
        mailVal: {
            get() {
                return this.mail
            },
            set(val) {
                const findMail = data.find((obj) => obj.mailName.toLowerCase() === val.toLowerCase())
                if (findMail) {
                    val = `${findMail.mailName}@inv.mn.edu`
                    this.isVisible = true
                }
                this.$emit('update:mail', val)
                if (this.mailModifiers.check) {
                    if (!findMail) this.$refs.inp.style.backgroundColor = 'red'
                    else this.$refs.inp.style.backgroundColor = 'transparent'
                }
            },
        },
    },
    methods: {
        clearInput() {
            this.isVisible = false
            this.$refs.inp.focus()
            this.$nextTick(() => {
                this.$refs.inp.value = ''
            })
        },
    },
}
</script>
<style lang="scss" scoped></style>
