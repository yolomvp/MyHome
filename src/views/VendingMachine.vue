<template>
    <div class="body-container">
    <div class="vending-machine">
      <div class="box">
        <div class="box-container">
          <div class="box-container__container">
            <table class="table">
              <tbody>
                <tr
                  v-for="(row, index) in items"
                >
                  <vending-item 
                    v-for="(item, itemIndex) in row"
                    :item="item"
                    @click="buyItem(item)"
                  />
                  
                </tr>
              </tbody>
            </table>
          </div>
          <div class="box-container__sidebar">
            <div class="grid">
              <div class="grid__value">{{ userBalance }}</div>
              <button @click="insert()">Внести</button>
              <input class="grid__input" 
              type="text"
              :placeholder="placeholder"
              v-model="inputValue"
              >
            </div>
            <div class="grid">
              <button @click="getСhange()">Забрать сдачу</button>
            </div>
          </div>
        </div>
        <div class="box__push"></div>
      </div>
    </div>
    <ul class="list">
      <!-- <li class="list__item" v-for="purchased in purchasedItems">
        {{ purchased  }}
      </li> -->
    </ul>
  </div>
</template>

<script>
import VendingItem from '@/components/VendingItem.vue'
export default {
  name: "VendingMachine",
  components: {
    VendingItem,
  },
  data() {
    return {
      items: [
        [{
            imagePath: './images/cheetos.png',
            id: 1,
            price: 120,
            count: 5,
          },
          {
            imagePath: './images/cheetosNew.png',
            id: 2,
            price: 140,
            count: 5,
          },
          {
            imagePath: './images/ruzik.png',
            id: 3,
            price: 100,
            count: 5,
          },
          {
            imagePath: './images/chocoPie.png',
            id: 4,
            price: 180,
            count: 5,
          },
        ],

        [{
            imagePath: './images/hrusTeam.png',
            id: 5,
            price: 110,
            count: 5,
          },
          {
            imagePath: './images/hrusTeamNew.png',
            id: 6,
            price: 120,
            count: 5,
          },
          {
            imagePath: './images/ruzikBig.png',
            id: 7,
            price: 250,
            count: 5,
          },
          {
            imagePath: './images/lays.png',
            id: 8,
            price: 100,
            count: 5,
          },
        ],

        [{
            imagePath: './images/laysBecon.png',
            id: 9,
            price: 100,
            count: 5,
          },
          {
            imagePath: './images/laysClassic.png',
            id: 10,
            price: 75,
            count: 5,         
          },
          {
            imagePath: './images/marmeladChup.png',
            id: 11,
            price: 35,
            count: 5,          
          },
          {
            imagePath: './images/laysNew.png',
            id: 12,
            price: 90,
            count: 5,          
          },
        ],

        [{
            imagePath: './images/haribo.png',
            id: 13,
            price: 30,
            count: 5,          
          },
          {
            imagePath: './images/m&m.png',
            id: 14,
            price: 85,
            count: 5,          
          },
          {
            imagePath: './images/tarallini.png',
            id: 15,
            price: 65,
            count: 5,          
          },
          {
            imagePath: './images/taralliniNew.png',
            id: 16,
            price: 50,
            count: 5,          
          },
        ],
      ],
      placeholder: 'Внесите деньги',
      userBalance: 0,
      inputValue: null,
      machineBalance: {
        500: 2,
        100: 10,
        50: 20,
        10: 100,
        5: 200,
        1: 200,
      },
      purchasedItems: [
        {
          id:1,
          purchasedName: 'cheetos',
          count: 0,
        },
        {
          id:2,
          purchasedName: 'cheetosNew',
          count: 0,
        },
        {
          id:3,
          purchasedName: 'ruzik',
          count: 0,
        },
        {
          id:4,
          purchasedName: 'chocoPie',
          count: 0,
        },
        {
          id:5,
          purchasedName: 'hrusTeam',
          count: 0,
        },
        {
          id:6,
          purchasedName: 'hrusTeamNew',
          count: 0,
        },
        {
          id:7,
          purchasedName: 'ruzikBig',
          count: 0,
        },
        {
          id:8,
          purchasedName: 'lays',
          count: 0,
        },
        {
          id:9,
          purchasedName: 'laysBecon',
          count: 0,
        },
        {
          id:10,
          purchasedName: 'laysClassic',
          count: 0,
        },
        {
          id:11,
          purchasedName: 'marmeladChup',
          count: 0,
        },
        {
          id:12,
          purchasedName: 'laysNew',
          count: 0,
        },
        {
          id:13,
          purchasedName: 'haribo',
          count: 0,
        },
        {
          id:14,
          purchasedName: 'm&m',
          count: 0,
        },
        {
          id:15,
          purchasedName: 'tarallini',
          count: 0,
        },
        {
          id:16,
          purchasedName: 'taralliniNew',
          count: 0,
        },
      ]
    }
  },
  methods: {
    buyItem(item) {
     if (item.count && this.userBalance >= item.price) {
      item.count -= 1
      this.userBalance -= item.price
     }
    //  for (const purchased of this.purchasedItems) {
    //   if (item.id === purchased.id) {
    //   purchased.count += 1
    // } else {
    //   purchasedItems.push(purchased)
    // }
    },

    insert() {
      if (['50', '100', '500', '1000',].includes(this.inputValue)) {
        if (this.inputValue != 1000) {
        this.machineBalance[this.inputValue] += 1 }
        this.userBalance += +this.inputValue
        this.inputValue = null
      }
    },
    getСhange() {
      const change = {}
      for (const key in this.machineBalance) {
        if (this.userBalance / key >= 1) {
          const billsNumber = Math.floor(this.userBalance / key)
          if (this.machineBalance[key]) {
            change[key] = this.machineBalance[key] >= billsNumber ? billsNumber : this.machineBalance[key]
            this.userBalance -= change[key] * key
            this.machineBalance[key] -= change[key]
          }
        }
      }
      alert(`Ваша сдача${JSON.stringify(change)}`)
    },
  }
}
</script>
