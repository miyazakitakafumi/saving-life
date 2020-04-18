<template>
  <v-card max-width="344" outlined>
    <v-list-item>
      <v-list-item-content>
        <div class="overline mb-4">{{ category }}</div>
        <v-list-item-title class="headline mb-1">{{ name }}</v-list-item-title>
        <v-list-item-subtitle>
          <v-text-field
            label="price"
            type="number"
            v-model="price"
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
  props: ['item', 'index'],
  computed: {
    name: {
      get() {
        return this.$props.item.productName
      },
      set() {}
    },
    category: {
      get() {
        return this.$props.item.category
      },
      set() {}
    },
    price: {
      get() {
        return this.$props.item.price
      },
      set(price) {
        this.updateValue({ ...this.$props.item, price })
      }
    }
  },
  methods: {
    remove() {
      this.$emit('remove', this.index)
    },
    updateValue(value) {
      this.$emit('input', { value, index: this.$props.index })
    }
  }
}
</script>
