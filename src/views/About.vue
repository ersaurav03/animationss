<template>
  <div class="about">
    <h1>Animation 2</h1>
    <hr>
    <button class="btn btn-danger" @click="show =! show">Show Alert</button>
    <br><br>
<transition name="fade">
    <div class="alert alert-danger" v-if="show">
    	Her is also some information
    </div>
</transition>

    <transition name="slide">
    <div class="alert alert-danger" v-if="show">
    	Her is also some information
    </div>
     </transition>
     
  </div>
</template>

<script>
	export default{
		data(){
			return{
				show:false
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
      /*transform: translateY(20px);*/
	}
	.slide-enter-active{
      animation: slide-in 1s ease-out forwards;
	}
	.slide-leave{

	}
	.slide-leave-active{
     animation: slide-out 1s ease-out forwards;
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