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
              <input class="grid__input" type="text" placeholder="Внесите деньги">
              <button>Внести</button>
            </div>
            <div class="grid">
              <input class="grid__input" type="text" placeholder="Заберите сдачу">
              <button>Забрать</button>
            </div>
          </div>
        </div>
        <div class="box__push"></div>
      </div>
    </div>
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
            count: 0,
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
            count: 0,
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
            count: 0,          
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
            count: 0,          
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
      ]
    }
  },
  methods: {
    buyItem (item) {

    }
  }
}
</script>
