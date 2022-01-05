<template>
  <div>
    <h2>Manage Goals</h2>
    <input type="text" ref="goal">
    <button @click="setGoal()">SUBMIT</button>

    <!-- Error dialog teleported to body tag for semantics. -->
    <teleport to="body">
      <error-alert v-if="inputIsinvalid">
        <h2>Input INVALID</h2>
        <p>Please enter valid input!!!</p>
        <button @click="confirmError()">OK</button>
      </error-alert>
    </teleport>

  </div>
</template>

<script>
  import ErrorAlert from './ErrorAlert.vue'
  
  export default {
    components: {
      ErrorAlert
    },
    data() {
      return {
        inputIsinvalid: false
      }
    },
    methods: {
      setGoal() {
        const inputGoal = this.$refs.goal.value
        if (!inputGoal) {
          this.inputIsinvalid = true
        }
      },
      confirmError() {
        this.inputIsinvalid = false
      }
    }
  }
</script>