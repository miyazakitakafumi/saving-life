<template>
  <div>
    {{ name }} <br />
    {{ firstName }}
    <v-btn @click="firstName = 'bi-ba-'">firstName</v-btn> <br />
    {{ lastName }}
    <v-btn @click="lastName = 'myz'">lastName</v-btn> <br />
    {{ birthday }}
    <v-btn @click="updateBirtyday('2000-01-01')">birthday</v-btn> <br />
  </div>
</template>

<script>
export default {
  name: 'Test',
  data: () => ({
    value: {
      name: {
        firstName: 'takafumi',
        lastName: 'miyazaki'
      },
      birthday: '1987-10-28'
    }
  }),
  computed: {
    name: {
      get() {
        return this.value.name
      },
      set() {
        this.value.name = name
      }
    },
    firstName: {
      get() {
        return this.value.name.firstName
      },
      set(firstName) {
        this.value.name = { ...this.value.name, firstName }
      }
    },
    lastName: {
      get() {
        return this.value.name.lastName
      },
      set(lastName) {
        this.value.name = { ...this.value.name, lastName }
      }
    },
    birthday: {
      get() {
        return this.value.birthday
      },
      set(birthday) {
        this.value.birthday = birthday
      }
    }
  },
  methods: {
    updateBirtyday(birthday) {
      this.birthday = birthday
    }
  }
}
</script>
