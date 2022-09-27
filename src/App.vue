<template>
  
  <RampCurved msg="Ramp Curve test"/>
</template>

<script>
import RampCurved from './components/ramp_curve.vue'

export default {
  name: 'App',
  components: {
    RampCurved
  },
  data () {
    return {
      msg: "Ramp Curve test "
    }
  }
}
</script>

<style>
#app, template {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: rgba(60, 57, 57, 0.627);
  height: 100vh;
  width: 100vw;
}
</style>
