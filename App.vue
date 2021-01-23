<template>
  <form action="" @submit="onSubmit">
    <c-input
        name="Username"
        type="text"
        :rules="{required: true, min: 6}"
        @onUpdate="onUpdate"
        :value="username.value" />
    <c-input
        name="Password"
        type="password"
        :rules="{required: true, min: 8}"
        @onUpdate="onUpdate"
        :value="password.value" />
    <c-input
        name="Mobile"
        type="tel"
        :rules="{required: true, min: 10}"
        @onUpdate="onUpdate"
        :value="mobile.value" />
    <c-button
        text="Register"
        color="white"
        background="green"
        :disabled="!valid" />
  </form>
</template>

<script>
import CButton from './components/CButton.vue';
import CInput from './components/CInput.vue';
export default {
  components: {
    CButton,
    CInput
  },
  data(){
    return {
      username: {
        value: '',
        valid: false
      },
      password: {
        value: '',
        valid: false
      },
      mobile: {
        value: '',
        valid: false
      }
    }
  },
  methods: {
    onUpdate(data) {
      this[data.name.toLowerCase()] = {
        value: data.value,
        valid: data.valid
      }
    },
    onSubmit(e){
      e.preventDefault()
    }
  },
  computed: {
    valid(){
      return this.username.valid && this.password.valid && this.mobile.valid
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  width: 200px;
}
</style>