<template>
	<li>
		<img @click="animate" src="@/assets/imgs/arcade-machine.svg" class="machine">
		<div class="coin-overflow" :class="coinInside ? 'inside' : ''">
			<img :src="require(`@/assets/imgs/coin-${type}.svg`)">
		</div>
		<div class="product-overflow" :class="productInside ? 'inside' : ''">
			<img :src="require(`@/assets/imgs/product-${type}.svg`)">
		</div>
	</li>
</template>

<script>
export default {
	name: 'ArcadeAnimation',
	props: ['type'],
	methods: {
		animate(){
			this.coinInside = true;
			setTimeout(()=>{
				this.productInside = false;
				setTimeout(()=>{
					this.productInside = true;
					setTimeout(()=>{
						this.reset();
					},1000);
				},1000);
			},1000);
		},
		reset(){
			this.coinInside = false;
			this.productInside = true;
		},
		getRandomTimer(min, max) {
			min = Math.ceil(min);
			max = Math.floor(max);
			return Math.floor(Math.random() * (max - min)) + min;;
		}
	},
	mounted(){
		setTimeout(()=>{
			this.animate();
			setInterval(()=>{
				this.animate();
			},5000);
		}, this.type * 100); // use this.type * this.getRandomTimer(100,500) to make to machines start randomly
	},
	data() {
		return{
			coinInside : false,
			productInside : true,
		}
	}
}
</script>

<style scoped>
li{
	position: relative;
	float: right;
	transform: skew(0deg,30deg);
    margin-right: -145px;
}
li img.machine{
	width: 240px;
	position: relative;
}
li .coin-overflow{
	position: absolute;
    width: 75px;
    height: 100px;
    left: 105px;
    top: 118px;
    transform: skew(0deg,-31deg);
    overflow: hidden;
}
li .coin-overflow img{
    transform: skew(0deg,31deg);
    width: 32px;
    margin-top: 12px;
    position: absolute;
    left: 20px;
    top: 20px;
	transition: all .4s cubic-bezier(0.31, -1.105, 0.43, 1.4) 0.4s;
}
li .coin-overflow.inside img{
    left: -40px;
    top: -40px;
}
li .product-overflow{
	position: absolute;
	width: 52px;
    left: 30px;
    bottom: 271px;
    transform: skew(0deg,-30deg);
    height: 140px;
    overflow: hidden;
}
li .product-overflow img{
	transform: skew(0deg,30deg);
	transition: all .4s cubic-bezier(0.31, -1.105, 0.43, 1.4) 0.4s;
	position: absolute;
	bottom: 15px;
}
li .product-overflow.inside img{
	bottom: -90px;
}
</style>
