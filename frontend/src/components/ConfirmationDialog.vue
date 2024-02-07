<!-- ConfirmationDialog.vue -->
<template>
  <div v-if="show" class="confirmation-overlay">
    <div class="confirmation-box">
      <h2>Confirmation</h2>
      <p>{{ message }}</p>
      <div class="actions">
        <button @click="confirm">Confirm</button>
        <button @click="cancel">Cancel</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      required: true
    },
    message: {
      type: String,
      default: 'Are you sure you want to proceed?'
    }
  },
  methods: {
    confirm() {
      this.$emit('confirm');
    },
    cancel() {
      this.$emit('cancel');
    }
  }
}
</script>

<style scoped>
.confirmation-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}
.confirmation-box {
  background: #fff;
  padding: 20px;
  border-radius: 5px;
  width: 90%;
  max-width: 500px;
}
.actions {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}
</style>
