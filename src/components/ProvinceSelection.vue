<template>
	<div class="province-selection">
		<InputBox @showList="showList"> </InputBox>
		<ListDropdown @showList="showList" :isShow="isShow" :apiFromProvinceSelection="apiFromApp" @updateProvince="handleSelected"></ListDropdown>
		<div v-show="showResultBox" class="result-box"> 
			<div v-for="(province,index) in selectedProvince" :key="index" class="result__item">
				<p> {{ province }} </p>
				<img @click="deleteProvince(index)" src="../assets/close.png">
			</div>
		</div>
	</div>
</template>

<script>
import InputBox from './InputBox.vue'
import ListDropdown from './ListDropdown.vue'

export default {
	name: 'ProvinceSelection',
	components: {
		InputBox,
		ListDropdown,
		// ResultBox
	},
	data() {
		return {
			selectedProvince: [],
			isShow: false,
		}
	},
	computed:{
		showResultBox(){
			return this.selectedProvince.length 
		}
	},
	props: {
		apiFromApp: Array,
	},
	methods: {
		handleSelected(event) {
			this.selectedProvince = event;
		},
		showList(){
			this.isShow = !this.isShow;
			// console.log(this.isShow);
		},
		deleteProvince(index){
			this.selectedProvince.splice(index, 1);
		}

	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.province-selection {
	margin: auto;
	width: 480px;
	box-sizing: border-box;
}

.result-box {
	display: relative;
	border: 1px solid #999999;
	margin-top: 8px;
	min-height: 48px;
	width: 480px;
	cursor: pointer;
	align-items: center;
	border-radius: 4px;

	display: flex;
	flex-wrap: wrap;
}

.result__item {
	position: relative;
	max-width: 199px;
	min-height: 32px;
	background-color: #F8F8F8;
	border-radius: 32px;

	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
	margin: 8px 4px 8px 8px;
}

.result__item p {
	/* line-height: 24px; */
	color: #333333;
	margin: 0px 0px 0px 16px;
}
/* close button */
.result-box img {
	width: 11px;
	height: 11px;
	margin: 0px 11px 0px 11px;
}
</style>
