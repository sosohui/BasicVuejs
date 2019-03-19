<template>
  <div class="red lighten-3 pa-3">
    <h3>자세한 회원 정보를 확인합니다.</h3>

    <v-list dense>
      <v-list-tile>
        <v-list-tile-content>이름 : </v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ name }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>주소 : </v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ address }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>전화번호 : </v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ phone }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>수정일자 : </v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ getDateAndTime(editedDate) }}
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </div>
</template>

<script>
//arrow함수를 써야 this로 사용 가능
  import { eventBus } from "../main"
  import { dateFormat } from '../mixins/dateFormat'

  export default {
    date() {
      return {
        editedDate: null
      }
    },
    props:
      ['name','address','phone'],
    created() {
      eventBus.$on('userWasEdited', date => {
        this.editedDate = date
      })
    },
    methods: {
      // getDateAndTime(date) {
      //   if (date !== null){
      //     let hour = date.getHours()
      //     let minutes = date.getMinutes()
      //     let fullDate = `${date.getFullYear()}/${date.getMonth()+1}/${date.getDate()}`
      //     return `${fullDate} ${hour}:${minutes}`
      //   }else{
      //     return null
      //   }
      // }
    },
    mixins: [dateFormat]
  }
</script>
