<script lang="ts">
import VueCounter from './components/VueCounter.vue'
import UserCard from '../../sandbox/src/components/UserCard.vue'

export default {
  components: {
    VueCounter,
    UserCard,
  },
  data() {
    return {
      message: 'Hello Vue!',
      listOfNumbs: [
        {
          name: 0,
          id: 'b674c468-5b91-49cb-b5a3-5981837ed977',
          list: [1, 2, 3],
        },
        {
          name: 1,
          id: 'd85a011b-f95b-47bf-b7a8-504b46e6cc96',
          list: [1, 2, 3],
        },
        {
          name: 2,
          id: 'e697c72a-6c8c-495a-b76a-64a7238b4d21',
          list: [1, 2, 3],
        },
        {
          name: 3,
          id: 'bcd679d9-3898-468d-a2b6-7adc95130802',
          list: [1, 2, 3],
        },
        {
          name: 4,
          id: 'a0b25edd-ed61-4e76-8fac-0bc7c07bb053',
          list: [1, 2, 3],
        },
      ],
      userData: {
        name: 'Ben',
        preferredFramework: 'Vue',
        favoriteFood: 'sushi',
        favoriteNumbers: [8, 10, 12],
      },
    }
  },
  methods:{
    changeName() {
      this.userData.name = "Charlie"
    }
  }
}
</script>

<template>
  <UserCard :user="userData" @change-name="changeName"/>
  <VueCounter />
  <!-- ! exercise 1 -->
  <p v-if="message.length % 2 === 0">Even: {{ message.toUpperCase() }}</p>
  <p v-else>Odd : {{ message }}</p>
  <ul>
    <li v-for="val in listOfNumbs" :key="val.id">
      {{ val.name }}
      <ul>
        <li v-for="(num, index) in val.list" :key="index">{{ num }}</li>
      </ul>
    </li>
  </ul>
</template>

<style scoped></style>
