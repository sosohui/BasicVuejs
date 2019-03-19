<template>
  <div class="yellow lighten-3 pa-3">
    <h3>회원 정보를 수정할 수 있습니다.</h3>
    <p>수정사항</p>
    <v-text-field
      label="이름"
      v-model="user.name"
    ></v-text-field>
    <v-text-field
      label="주소"
      v-model="user.address"
    ></v-text-field>
    <v-text-field
      label="전화번호"
      v-model="user.phone"
    ></v-text-field>
    <v-btn @click="changeUser">수정 완료</v-btn>
  </div>
</template>

<script>
  import { eventBus } from "../main"
  export default {
    props: ["name","address","phone"],
    data () {
      return {
        user: {}
      }
    },
    created() {
      this.user.name = this.name
      this.user.address = this.address
      this.user.phone = this.phone
    },
    methods: {
      changeUser() {
        this.$emit("child",this.user)
        // console.log(this.user)
        // eventBus.$emit("userWasEdited",new Date())
        eventBus.userWasEdited(new Date())
      }
    }
  }
</script>
