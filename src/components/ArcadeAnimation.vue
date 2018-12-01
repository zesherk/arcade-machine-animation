<template>
	<div id="animated-arcade">
		<div class="toggle-animation" :class="showAnimation? 'small' : ''" @click="toggleAnimation">
			<template v-if="showAnimation">
				<span>Stop me</span>
				<div class="icon">
					<img src="@/assets/imgs/icon-stop.svg" class="icon-play">
				</div>
			</template>
			<template v-else>
				<span>Play me !</span>
				<div class="icon">
					<img src="@/assets/imgs/icon-play.svg" class="icon-play">
				</div>
			</template>
		</div>
		<div v-if="showAnimation" class="animation-container">
			<ul class="machines">
				<ArcadeMachine v-for="index in [1,2,3]" :type="index" />
			</ul>
			<img src="@/assets/imgs/player.svg" class="player">
			<img src="@/assets/imgs/floor.svg" class="floor">
		</div>
	</div>
</template>

<script>
import ArcadeMachine from './ArcadeMachine.vue'

export default {
	name: 'ArcadeAnimation',
	components:{
		ArcadeMachine
	},
	methods:{
		toggleAnimation(){
			this.showAnimation = !this.showAnimation;
		}
	},
	data(){
		return{
			showAnimation : false
		}
	}
}
</script>

<style>
#animated-arcade{
	background-image: linear-gradient(134deg,#FF7749 0,#FF3A68 100%);
	width: 100%;
	min-width: 1000px;
	min-height: 654px;
	height: 100%;
	display: inline-block;
}
.animation-container{
	width: 1000px;
	height: 654px;
	position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    display: block;
    margin: auto;
	animation: jelly 1s linear both;
}
.floor{
	position: absolute;
	bottom: 0;
	z-index: 0;
}
.machines{
	position: absolute;
	bottom: 100px;
	z-index: 1;
	position: absolute;
	left: 50%;
	top: 50%;
	transform: skew(0deg,-30deg) translate(-50%,-50%);
    margin-top: -60px;
    margin-left: 15px;
}
.player{
	position: absolute;
    width: 170px;
    right: 110px;
    bottom: 100px;
    z-index: 100;
}

/* Button style */
.toggle-animation {
    display: block;
    background: #6433ac;
    width: 300px;
    height: 100px;
    line-height: 100px;
    margin: auto;
    color: #fff;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    cursor: pointer;
    overflow: hidden;
    border-radius: 50px;
    box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.3);
    transition: all .25s cubic-bezier(0.31, -0.105, 0.43, 1.4), line-height 1ms;
    z-index: 999;
    animation: jelly 1s linear both;
}
.toggle-animation.small{
	width: 200px;
    height: 54px;
    line-height: 50px;
    bottom: 70px;
    top: unset;
}
.toggle-animation:hover{
	background: #6f3cb9;
}
.toggle-animation span {
    width: 72%;
    line-height: inherit;
    font-size: 22px;
    left: 0;
    transition: all 0.25s cubic-bezier(0.31, -0.105, 0.43, 1.4);
}
.toggle-animation span:after{
    content: '';
    background-color: #fff;
    width: 1px;
    height: 40%;
    position: absolute;
    top: 30%;
    right: -1px;
}
.toggle-animation .icon{
    width: 28%;
    right: 0;
    transition: all 0.25s cubic-bezier(0.31, -0.105, 0.43, 1.4);
}
.toggle-animation span, 
.toggle-animation .icon{
    display: block;
    height: 100%;
    text-align: center;
    position: absolute;
    top: 0;
}
.toggle-animation:hover span{
    left: -72%;
    opacity: 0;
}
.toggle-animation:hover .icon{
    width: 100%;
}
.toggle-animation:hover .icon img{
    height: 46px;
}
.toggle-animation .icon img{
    height: 36px;
}
.toggle-animation.small .icon img{
    height: 30px;;
}
.toggle-animation .icon img{
    font-size: 30px;
    vertical-align: middle;
    transition: all 0.25s cubic-bezier(0.31, -0.105, 0.43, 1.4), height 0.25s ease;
}

/* Generated with Bounce.js. Edit at https://goo.gl/Vn2Euz */
@keyframes jelly { 
 	0% { transform: matrix3d(0.5, 0, 0, 0, 0, 0.5, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	3.4% { transform: matrix3d(0.658, 0, 0, 0, 0, 0.703, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	4.7% { transform: matrix3d(0.725, 0, 0, 0, 0, 0.8, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	6.81% { transform: matrix3d(0.83, 0, 0, 0, 0, 0.946, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	9.41% { transform: matrix3d(0.942, 0, 0, 0, 0, 1.084, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	10.21% { transform: matrix3d(0.971, 0, 0, 0, 0, 1.113, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	13.61% { transform: matrix3d(1.062, 0, 0, 0, 0, 1.166, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	14.11% { transform: matrix3d(1.07, 0, 0, 0, 0, 1.165, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	17.52% { transform: matrix3d(1.104, 0, 0, 0, 0, 1.12, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	18.72% { transform: matrix3d(1.106, 0, 0, 0, 0, 1.094, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	21.32% { transform: matrix3d(1.098, 0, 0, 0, 0, 1.035, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	24.32% { transform: matrix3d(1.075, 0, 0, 0, 0, 0.98, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	25.23% { transform: matrix3d(1.067, 0, 0, 0, 0, 0.969, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	29.03% { transform: matrix3d(1.031, 0, 0, 0, 0, 0.948, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	29.93% { transform: matrix3d(1.024, 0, 0, 0, 0, 0.949, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
 	35.54% { transform: matrix3d(0.99, 0, 0, 0, 0, 0.981, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	36.74% { transform: matrix3d(0.986, 0, 0, 0, 0, 0.989, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	41.04% { transform: matrix3d(0.98, 0, 0, 0, 0, 1.011, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	44.44% { transform: matrix3d(0.983, 0, 0, 0, 0, 1.016, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	52.15% { transform: matrix3d(0.996, 0, 0, 0, 0, 1.003, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	59.86% { transform: matrix3d(1.003, 0, 0, 0, 0, 0.995, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	63.26% { transform: matrix3d(1.004, 0, 0, 0, 0, 0.996, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	75.28% { transform: matrix3d(1.001, 0, 0, 0, 0, 1.002, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	85.49% { transform: matrix3d(0.999, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	90.69% { transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); }
	100% { transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1); } 
}
</style>
