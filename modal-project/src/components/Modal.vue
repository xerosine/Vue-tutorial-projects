<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal">
             <slot>Cool Modal</slot>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        closeModal() {
            this.$emit("close");
        }
    }
}
</script>

<style>
    .modal {
        height: 100px;
        width: 300px;
        background-color: white;
        border-radius: 5px;
        padding: 20px;
        margin: 120px auto;
    }

    .backdrop {
        position: fixed;
        top: 0;
        left: 0;
        height: 100%;
        width: 100%;
        background-color: rgba(0, 0, 0, 0.5);
    }
</style>