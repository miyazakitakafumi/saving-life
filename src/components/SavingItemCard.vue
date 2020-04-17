<template>
  <v-card max-width="344" outlined>
    <v-list-item>
      <v-list-item-content>
        <div class="overline mb-4">{{ savingItem.category }}</div>
        <v-list-item-title class="headline mb-1">{{
          savingItem.productName
        }}</v-list-item-title>
        <v-list-item-subtitle>
          <v-text-field
            label="price"
            type="number"
            v-model="savingItem.price"
          ></v-text-field>
        </v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>

    <v-card-actions>
      <v-btn @click="remove" text>削除する</v-btn>
      <v-btn text>変更する</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'SavingItemCard',
  props: ['savingItem', 'savingItemKey'],
  data: () => ({
    //
  }),
  methods: {
    remove: function() {
      this.$emit('remove', this.savingItemKey)
    }
  }
}
</script>
