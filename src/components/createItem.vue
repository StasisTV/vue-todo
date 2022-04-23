<template>
  <div>
      <button v-on:click="submit">+</button>
      <input v-on:keydown.enter="submit" type="text" ref="userInput">
  </div>
</template>

<script>
    export default {
        methods: {
            submit() {
                let val = this.$refs.userInput.value; 
                if(val != "") {
                    this.$refs.userInput.value = "";
                    this.$emit("newItem", val);
                }
            }
        }
    }
</script>

<style lang="scss">
button {
    border-radius: 22%;
    margin-right: 1vw;
}

input {
    border-radius: 0.25rem;
}
</style>