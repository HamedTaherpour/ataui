<template>
    <div>
        <button @click="isOpen = !isOpen">
            <slot name="header"></slot>
        </button>
        <transition name="slide-fade">
            <div v-show="isOpen">
                <slot/>
            </div>
        </transition>
    </div>
</template>

<script setup>
import {ref} from "@vue/reactivity";

const isOpen = ref(false);
</script>

<style scoped>
/*
  Enter and leave animations can use different
  durations and timing functions.
*/
.slide-fade-enter-active {
    transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
    transition: all 0.2s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateY(-20px);
    opacity: 0;
}
</style>
