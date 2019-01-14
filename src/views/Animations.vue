<template>
<div class="container">
		<!-- <h1 class="text-primary">JSMPJ Corporation</h1> -->
		<h1>Aminations</h1>
		<hr>

		<select v-model="alertAnimation" class="form-control">
			<option value="fade">Fade</option>	
			<option value="slide">Slide</option>
		</select>
		<button class="btn btn-primary" @click="show =! show">Show Alert</button>
		<br><br>

		<transition :name="alertAnimation">
			<div class="alert alert-info" v-if="show">
				Here Is Some Information 1
			</div>
		</transition>

		<transition :name="alertAnimation" type="animation">
			<div class="alert alert-info" v-if="show">
				Here Is Some Information 1
			</div>
		</transition>

		<transition appear
		enter-class=""
		enter-active-class="animated pulse"
		leave-class=""
		leave-active-class="animated zoomOut"
		>
		<div class="alert alert-info" v-if="show">
			Here Is Some Information 1
		</div>
	    </transition>


	    <transition :name="alertAnimation" mode="out-in">
			<div class="alert alert-info" v-if="show" key="info">Here Is Some Information about informaion</div>

			<div class="alert alert-warning" v-else key="warning">Here Is Some Information about warning</div>
		</transition>

</div>
</template>
<script>
	export default{
		data(){
			return{
				show: true
			}
		}
	}
</script>

<style>
.fade-enter{
	opacity: 0;
}
.fade-enter-active{
	transition: opacity 1s;
}
.fade-leave{

}
.fade-leave-active{
	transition: opacity 1s;
	opacity: 0;
}

.slide-enter{
	opacity: 0;
	/*transform: translateY(20px);*/
}
.slide-enter-active{
	animation: slide-in 1s ease-out forwards;
	transition: opacity 0.5s;
}
.slide-leave{

}
.slide-leave-active{
	animation: slide-out 1s ease-out forwards;
	transition: opacity 1s;
	opacity: 0;
}

@keyframes slide-in {
	from{
		transform: translateY(20px);
	}
	to{
		transform: translateY(0);
	}
}
@keyframes slide-out {
	from{
		transform: translateY(0);
	}
	to{
		transform: translateY(20px);
	}

}
</style>