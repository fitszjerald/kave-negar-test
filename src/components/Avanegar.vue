
<template>
  <v-container>
		<v-card >
    <v-row class="px-5 pt-5">
			<v-col cols="3" class="align-self-center text-center">
				<h4>حداکثر تماس همزمان</h4>
			</v-col>
      <v-col cols="9">
        <v-slider
					class="mt-5"
          v-model="maxSimCall"
					:thumb-size="35"
          thumb-label="always"
					ticks="always"
					step="100"
					:max="1000"
					:min="100"
        >
				</v-slider>
      </v-col>

			<v-col cols="3" class="align-self-center text-center">
				<h4>میزان مکالمه (دقیقه)</h4>
			</v-col>
			<v-col cols="9">
        <v-slider
					class="mt-5"
          v-model="callAmountMinute"
					:thumb-size="39"
          thumb-label="always"
					ticks="always"
					step="1000"
					:max="100000"
					:min="10000"
        >
				</v-slider>
      </v-col>
			<v-col cols="3" class="align-self-center text-center">
				<h4>میزان نگهداری فایل مکالمه تماس (روز)</h4>
			</v-col>
			<v-col cols="9">
        <v-slider
					class="mt-5"
          v-model="saveCallDay"
					:thumb-size="35"
          thumb-label="always"
					ticks="always"
					step="1"
					:max="60"
					:min="1"
        >
				</v-slider>
      </v-col>
			<v-col cols="3" class="align-self-center text-center">
				<h4>میزان حجم ذخیره سازی اطلاعات (گیگابایت)</h4>
			</v-col>
			<v-col cols="9">
        <v-slider
					class="mt-5"
          v-model="storageVolume"
					:thumb-size="35"
					ticks="always"
          thumb-label="always"
					step="1"
					:max="100"
					:min="1"
					label=""
        >
				</v-slider>
      </v-col>
			<v-col cols="3">
				<v-spacer></v-spacer>
			</v-col>
			<v-col cols="4">
        <v-select
          v-model="selectMonth"
          :items="items"
          item-text="text"
          item-value="value"
          label="زمان بسته"
          return-object
          dense
          outlined
        ></v-select>
      </v-col>
    </v-row>
		<v-row justify="center">
			<v-col cols="3">
				<div>
					<v-btn large color="primary">پرداخت</v-btn>
				</div>
			</v-col>
			<v-col cols="3" align-self="center">
				<h3>
					<span>جمع کل فاکتور: </span>
					{{priceCal}}
					<span> تومان</span>
				</h3> 
			</v-col>
		</v-row>
		</v-card>
  </v-container>
</template>

<script>
import Avanegar from '@/components/Avanegar.vue'
export default {
  name: 'Home',
  components: {
    Avanegar
	},
	data () {
		return {
			maxSimCall: 100,
			callAmountMinute: 10000,
			saveCallDay: 1,
			storageVolume: 1,
			selectMonth: { text: '3 ماه', value: 3 },
        items: [
          { text: '3 ماه', value: 3 },
          { text: '6 ماه', value: 6 },
          { text: '1 سال', value: 10 }
        ],
		}
	},
	computed: {
		priceCal () {
			return ((this.callAmountMinute * 24) + ((this.maxSimCall/100) * 1000000) + (this.saveCallDay * 1000)) * this.selectMonth.value 
		}
	}
}
</script>