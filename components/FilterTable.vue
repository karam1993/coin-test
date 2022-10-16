<template>
  <div>
    <v-expansion-panels class="mb-2">
      <v-expansion-panel>
        <v-expansion-panel-header> Filter </v-expansion-panel-header>
        <v-expansion-panel-content>
          <v-row>
            <v-col cols="6">
              <v-autocomplete
                v-model="currency"
                :items="currencies"
                label="Currency"
                dense
                outlined
                @change="writeQuery"
              >
              </v-autocomplete>
            </v-col>
            <v-col cols="6">
              <v-autocomplete
                v-model="price_change_percentage"
                :items="price_change_percentageList"
                label="Price Changes"
                dense
                outlined
                @change="writeQuery"
              >
              </v-autocomplete>
            </v-col>
          </v-row>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-expansion-panels>
  </div>
</template>

<script>
export default {
  data() {
    return {
      price_change_percentageList: [
        "1h",
        "24h",
        "7d",
        "14d",
        "30d",
        "200d",
        "1y",
      ],
      currencies: ["usd", "eur", "jpy"],
      currency: "usd",
      price_change_percentage: "1h",
    };
  },
  methods: {
    writeQuery(){
        let query=`?vs_currency=${this.currency}&price_change_percentage=${this.price_change_percentage}&per_page=20`
        this.$emit('queryMethod' , query)
    }
  },
};
</script>