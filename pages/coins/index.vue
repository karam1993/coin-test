<template>
    <v-container>
        <v-data-table
            :headers="headers"
            :items="coinsList"
            :items-per-page="5"
            class="elevation-1"
        >
        <template v-slot:[`item.image`]="{ item }">
            <div>
                <v-img :src="item.image" width="40" class="ma-2"></v-img>
            </div>
        </template>
        <template v-slot:[`item.current_price`]="{ item }">
            <div>
                <v-chip color="primary">{{item.current_price}} $</v-chip>
            </div>
        </template>
        <template v-slot:[`item.last_updated`]="{ item }">
            <div >
                <p>{{ item.last_updated}} </p>
            </div>
        </template>
        <template v-slot:[`item.price_change_24h`]="{ item }">
            <div>
                <p v-if="item.price_change_24h.toFixed(2) > 0"><v-icon color="success">mdi-arrow-up-thick</v-icon><span>{{item.price_change_24h.toFixed(2)}}</span></p>
                <p v-else-if="item.price_change_24h.toFixed(2) < 0"><v-icon color="error">mdi-arrow-down-thick</v-icon><span>{{item.price_change_24h.toFixed(2)*-1}}</span></p>
                <p v-else><v-icon>mdi-equal</v-icon><span>{{item.price_change_24h.toFixed(2)*-1}}</span></p>
            </div>
        </template>
        </v-data-table>
    </v-container>
</template>



<script>
import dateFormat from 'dateformat'
  export default {
    data () {
      return {
        headers: [
          { text: 'Image', value: 'image' },
          { text: 'symbol', value: 'symbol' },
          { text: 'Coin Name', value: 'name', },
          { text: 'Last Update', value: 'last_updated' },
          { text: 'Price', value: 'current_price' },
          { text: '24 Last Changes', value: 'price_change_24h' },
        ],
        coinsList:[]
      }
    },
    created() {
        this.getCoinsList()
    },
    methods: {
        getCoinsList(){
            this.$axios.get('https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd').then((res) => {
                this.coinsList = res.data
                this.coinsList.forEach(element => {
                    element.last_updated=dateFormat(element.last_updated)
                });
            }).catch((err) =>{
                console.log(err)
            }).finally(()=>{

            })
        }
    },
  }
</script>