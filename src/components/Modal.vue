<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal">
            <h3>{{ exp1 }}</h3>
            <slot>defualt content</slot>
            <slot name="links"></slot>
        </div>
    </div>
</template>

<script>
export default {
    props: ['exp1'],
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>

<style>
.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
}

.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;

}
</style>