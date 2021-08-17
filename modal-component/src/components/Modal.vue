<template>
  <transition name="modal-ani">
    <div class="modal" v-show="isModalActive">
      <img
        class="modal__close"
        src="@/assets/svg/close-icon.svg"
        @click="close"
        alt="close"
      />
      <slot />
      <button @click="close">Close</button>
    </div>
  </transition>
</template>

<script>
export default {
  props: ["isModalActive"],
  setup(props, { emit }) {
    const close = () => {
      emit("closeEmit");
    };

    return {
      close,
    };
  },
};
</script>

<style lang="scss" scoped>
.modal {
  background: #297f87;
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  width: 400px;
  padding: 10px;
  border-radius: 20px;

  @include mq(sm, max) {
    width: 90%;
  }

  &__close {
    position: absolute;
    right: 5px;
    top: 5px;
    cursor: pointer;
  }
}

.modal-ani {
  &-enter-active,
  &-leave-active {
    transition: opacity 0.5s;
  }

  &-enter-from,
  &-leave-to {
    opacity: 0;
  }

  &-enter-to,
  &-leave-from {
    opacity: 1;
  }
}
</style>