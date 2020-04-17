<template>
  <v-row>
    <v-col>
      <saving-item-card v-for="(item, key) in savingItems" :saving-item="item" :key="key" :saving-item-key="key" @remove="removeItem"/>
    </v-col>
    <v-col>
    </v-col>
  </v-row>
</template>

<script>
import SavingItemCard from '../components/SavingItemCard'

export default {
  name: 'Home',
  components: { SavingItemCard },
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
      },
    ]
  }),
  methods: {
    removeItem: function(key){
      this.savingItems = this.savingItems.filter((d, k) => k !== key)
    }
  }
}
</script>
