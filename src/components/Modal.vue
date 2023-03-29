<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div @click.self="closeModal" class="backdrop">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- <h1>{{ header }}</h1>
      <p>{{ text }}</p> -->
      <slot></slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["header", "text", "theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(19, 15, 15, 0.5);
}

/* Styling for the modal itself */
.modal {
  width: 400px;
  background-color: #fff;
  border-radius: 10px;
  padding: 120px;
  margin: 300px auto;
  box-shadow: 0 3px 9px rgba(31, 30, 30, 0.5);
}
.modal h1 {
  color: rgb(138, 179, 230);
  border: none;
  padding: 0;
}
.modal.sale {
  color: rgb(50, 41, 41);
  background: rgb(194, 138, 138);
}
.modal .actions a {
  text-align: center;
  padding: 8px;
  margin: 30px 0 10px 0;
  color: #333;
}
</style>
