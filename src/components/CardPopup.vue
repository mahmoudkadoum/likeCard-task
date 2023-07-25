<script setup>
const props = defineProps({
    isOpen: Boolean,
    theCard: Object,
});

const emit = defineEmits([
  'setIsOpen',
]);

const onClose = () => {
    emit('setIsOpen', false)
};
</script>

<template>
    <div>
        <Transition>  
        <div v-if="props.isOpen">
            <div class="overlay" @click="onClose">
            <div class="modal">
                <img :src="props.theCard.src" alt="">
                <h1>{{props.theCard.title}}</h1>
            </div>
            </div>
        </div>
        </Transition>
    </div>
</template>

<style scoped>
.modal {
  width: 500px;
  margin: 0px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px 3px;
  transition: all 0.2s ease-in;
  font-family: Helvetica, Arial, sans-serif;
}
.fadeIn-enter {
  opacity: 0;
}

.fadeIn-leave-active {
  opacity: 0;
  transition: all 0.2s step-end;
}

.fadeIn-enter .modal,
.fadeIn-leave-active.modal {
  transform: scale(1.1);
}
.modal img {
    width: 100%;
}
button {
  padding: 7px;
  margin-top: 10px;
  background-color: green;
  color: white;
  font-size: 1.1rem;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #00000094;
  z-index: 999;
  transition: opacity 0.2s ease;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

</style>