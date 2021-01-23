<template>
  <div>
    <label
        :for="name"
    >{{ name }}
    </label>
    <input
        :id="name"
        :type="type"
        :value="value"
        @input="input"
    >
    <div class="error" v-if="error">
      {{error}}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {type: String, required: true},
    type: {type: String, required: true},
    value: {type: String},
    rules: {type: Object, required: true}

  },
  methods: {
    input(e) {
      this.$emit('onUpdate', {
        name: this.name,
        value: e.target.value,
        valid: this.validate(e.target.value) ? false : true
      })
    },
    validate(value) {
      if (this.rules.required && !value){
        return 'required'
      }
      if (this.rules.min && value.length < this.rules.min){
        return `${this.name} must be > ${this.rules.min}`
      }
    }
  },
  computed: {
    error(){
      return this.validate(this.value)
    }
  }
}
</script>

<style scoped>
.error {
  color: red;
  font-size: 11px;
}

input{
  padding: 5px;
  border: 1px solid lightgray;
  border-radius: 5px;
  margin: 5px 0;
  width: 100%;
}
label {
  display: flex;
  justify-content: space-between;
}
</style>