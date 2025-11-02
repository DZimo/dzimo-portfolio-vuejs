<template>
  <div class="modal-backdrop" @click.self="$emit('close')">
    <div class="modal-content">
      <button class="close-btn" @click="$emit('close')">&times;</button>
      <slot></slot>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: rgba(0, 0, 0, 0.5);
  padding: 1.5rem;
  border-radius: 8px;
  max-width: 600px;
  width: 90%;
  position: relative;
}

.close-btn {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  font-size: 1.5rem;
  border: none;
  background: none;
  cursor: pointer;
}
</style>
