<template>
  <h1>INDEX</h1>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HomeView',
  data() {
    return {
      categories_: [],
      isOrder_: false
    }
  },
  computed: {
    categories: {
      get() {
        if (this.categories_ != undefined) return this.categories_
        return []
      },
      set (newValue) {
        this.categories_ = newValue
      }
    },
    toPay() {
      let sum = 0
      this.categories.forEach(c => {
        c.products.forEach(p => {
            sum += p.amount * p.price
        })
      })

      return sum
    },
    isOrder: {
      get() {
        return this.isOrder_
      },
      set(val) {
        this.isOrder_ = val
      }
    }
  },
  created() {
    this.axios.get('https://api.1bot.edugid.org/category/list').then(response => {
      response.data.forEach(x => {    
        let category = {
          id: x.id,
          name: x.name,
          products: []
        }
        
        x.products.forEach(p => {
          category.products.push({
            id: p.id,
            name: p.name,
            description: p.description,
            price: p.price,
            img: p.img,
            amount: 0
          })
        })      

        this.categories.push(category)
      })
    })

    console.log(this.categories)
  }
});
</script>
