<template>
		<div class="block" v-if="showBlock" @click="stopTimer" >
			<span>Quick Click Here</span>
		</div>
</template>
	
<script>
export default{
	props:[
		"delay"
	],
	data(){ 
		return {
			showBlock: false,
			timer: null,
			score: 0
		}
	},
	mounted(){
		setTimeout(()=>{
			this.showBlock = true;
			this.startTimer();
		}, this.delay);
	},
	methods: {
		startTimer() {
			this.timer = setInterval(()=>{
			this.score+=50;
		}, 50)
		},
		stopTimer() {
			clearInterval(this.timer);
			this.$emit("endGame", this.score);
		}
	}
}
</script>
	
<style>
	.block {
		background-color: aqua;
		color: rgb(0, 105, 146);
		text-align: center;
		width: 300px;
		padding: 50px;
		margin: 30px auto;
		border-radius: 20px;
	}
</style>