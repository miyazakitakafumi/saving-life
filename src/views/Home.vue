<template>
  <v-container class="fill-height" fluid>
    <v-row>
      <v-col> Total: {{ sum }} </v-col>
    </v-row>
    <v-row>
      <v-col>
        <saving-item-card
          v-for="(item, key) in savingItems"
          :saving-item="item"
          :key="key"
          :saving-item-key="key"
          @remove="removeItem"
          @input="updateSavingItems"
        />
      </v-col>
      <v-col>
        <test />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import SavingItemCard from '../components/SavingItemCard'
import Test from '../components/Test'

export default {
  name: 'Home',
  components: { SavingItemCard, Test },
  data: () => ({
    savingItems: [
      {
        productName: 'お茶',
        category: '飲料',
        price: 130
      },
      {
        productName: 'コーラ',
        category: '飲料',
        price: 150
      },
      {
        productName: '水',
        category: '飲料',
        price: 100
      }
    ]
  }),
  methods: {
    removeItem: function(key) {
      this.savingItems = this.savingItems.filter((d, k) => k !== key)
    },
    updateSavingItems(updateObj) {
      this.savingItems = this.savingItems.map((item, index) => {
        if (index === updateObj.index)
          return {
            ...item,
            ...updateObj.value
          }
        return item
      })
    }
  },
  computed: {
    sum: function() {
      return this.savingItems.reduce((prev, current) => {
        return prev + (parseInt(current.price) || 0)
      }, 0)
    }
  }
}
</script>
