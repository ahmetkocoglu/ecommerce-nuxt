<script setup>
const emit = defineEmits(['modalClose']);

const props = defineProps({
    ModalOpen: Boolean,
});

const handleModalClose = () => {
    emit('modalClose', false);
}
</script>
<template>
    <dialog id="my_modal_1" class="modal" :class="{ 'modal-open': props.ModalOpen }">
        <div class="modal-box">
            <h3 class="font-bold text-lg">Hello!</h3>
            <p class="py-4">Press ESC key or click the button below to close</p>
            <div class="modal-action">
                <form method="dialog">
                    <button class="btn" @click="handleModalClose()">Close</button>
                </form>
            </div>
        </div>
    </dialog>
</template>