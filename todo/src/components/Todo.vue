<template>
  <b-button-group vertical>
    <b-button variant="outline-success" class="list-group-item text-left mt-2" @click="clickButton">
      {{ label }}
    </b-button>
  </b-button-group>
</template>
<script>
  export default {
    // 외부에서 입력받을 값props
    props: ['label'],
    methods: {
      clickButton() {
        this.$emit('componentClick')
      }
    }
  }
</script>

