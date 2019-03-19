<template>
  <div class="blue lighten-3 pa-3">
    <h1>User 컴포넌트</h1>
    <p>이름: {{ name }}</p>
    <p>{{ getDateAndTime(createdAt) }}</p>
    <p>{{ helloToMixin }}</p>
    <hr>
    <v-layout row wrap>
      <v-flex xs12 sm6>
        <UserDetail
          :name="name"
          :address="address"
          :phone="phone"
        ></UserDetail>
      </v-flex>
      <v-flex xs12 sm6>
        <UserEdit
        :name="name"
        :address="address"
        :phone="phone"
        @child="parents"
        ></UserEdit>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import UserDetail from "./UserDetail.vue"
import UserEdit from "./UserEdit.vue"
import { dateFormat } from '../mixins/dateFormat'

export default {
  components: {
    UserDetail,
    UserEdit
  },
  data() {
    return {
      name: 'soso',
      address: 'Daegu',
      phone: '1234-5678',
      createdAt : null
    }
  },
  created() {
    this.createdAt = new Date()
  },
  computed: {
    helloToMixin() {
      return this.mixinDate + '!!'
    }
  },
  methods: {
    parents(user) {
      this.name = user.name
      this.address = user.address
      this.phone = user.phone
      console.log("get Chlid!")
    },
    // getDateAndTime(date){
    //   let hour = date.getHours()
    //   let minutes = date.getMinutes()
    //   let fullDate = `${date.getFullYear()}/${date.getMonth()+1}/${date.getDate()}`
    //   return `${fullDate} ${hour}:${minutes}`
    // }
  },
  mixins: [dateFormat]
}
</script>
