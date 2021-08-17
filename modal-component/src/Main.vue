<template>
  <ModalComponent @closeEmit="toggleModal" :isModalActive="isModalActive">
    <div class="modal-content">
      <h1>Modal Header</h1>
      <p>Modal Paragraph</p>
    </div>
  </ModalComponent>
  <button @click="toggleModal" v-if="!isModalActive">Open</button>
</template>

<script>
import ModalComponent from "@/components/Modal.vue";
import { ref } from "vue";
export default {
  components: { ModalComponent },
  setup() {
    const isModalActive = ref(false);

    const toggleModal = () => {
      isModalActive.value = !isModalActive.value;
    };

    return {
      isModalActive,
      toggleModal,
    };
  },
};
</script>

<style lang="scss" >
.modal-content {
}
</style>
