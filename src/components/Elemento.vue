<template>
    <div class="elemento" @click="show(numid)">{{ element.name }}</div>
</template>

<script>
export default {
    name: 'FwElemento',
    props: {
        element: {
            type: Object,
            default: () => ({})
        },
        numid: {
            type: Number,
            default: 0
        }
    },
    computed: {
        preview() { return this.$parent.$parent.$refs.preview }
    },
    mounted() {
        document.head.innerHTML += `<link rel="prefetch"
                                href="${this.element.image}">`;
        this.$el.style.setProperty('--bgcolor', this.element.bgcolor);
    },
    methods: {
        show(id) { this.preview.setElement(this.element); }
    }
}
</script>

<style lang="postcss" scoped>
    .elemento {
        display        : flex;
        justify-content: center;
        align-items    : center;
        border         : 1px solid #fff;
        width          : 100px;
        height         : 100px;
        color          : #ddd;
        transition     : background 1s ease, color 0.2s ease-in-out;

        &:hover {
            background: var(--bgcolor);
            color: var(--textcolor);
            cursor: pointer;
        }
    }
</style>
