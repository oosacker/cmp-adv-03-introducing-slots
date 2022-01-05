<template>
  
  <dialog open>
    <slot></slot>
  </dialog>

</template>

<style scope>
  dialog {
    position: fixed;
    top: 20vh;
    left: 30%;
    width: 40%;

  }
</style>