<script>
import {ref, reactive} from 'vue';
export default{
  setup(){
    const images = reactive([
      {
        id: 1,
        path: "https://picsum.photos/1024/480/?image=58",
        title: "Image 1",
        label: "Lorem ipsum dolor sit amet, consectetur adipiscing elit."
      },
      {
        id: 2,
        path: "https://picsum.photos/1024/480/?image=62",
        title: "Image 2",
        label: "Aenean odio velit, consequat ac sodales sit amet."
      },
      {
        id: 3,
        path: "https://picsum.photos/1024/480/?image=50",
        title: "Image 3",
        label: "Mauris arcu ligula bibendum in lorem et tempor fringilla eros."
      },
        {
        id: 3,
        path: "https://picsum.photos/1024/480/?image=65",
        title: "Image 4",
        label: "Ligula bibendum in lorem et tempor fringilla tempor."
      },
    ]);
    const activeIndex = ref(0)
    const count =  images.length;

    function IncActiveIndex(){
      activeIndex.value +=1
      if(activeIndex.value == count){
        activeIndex.value = 0
      }
    }

    const interval = setInterval(IncActiveIndex, 3500);

    return {images,activeIndex,interval,IncActiveIndex}
  }
}
</script>

<template>
<p class="tit-font">Carousel</p><br>
  <div v-for="(val, index) in images" :key="index" 
    class="relative w-full overflow-hidden after:clear-both after:block ">

      <img :src="val.path" class="block w-full fade-in" alt="..." v-show="activeIndex==index" />

      <div v-show="activeIndex==index"
        class="absolute inset-x-[25%] bottom-5 hidden py-5 text-center text-white md:block">
        <h5 class="text-xl">{{ val.title }}</h5>
        <p>{{ val.label }}</p>
      </div>
  </div>

  <div
    class="absolute bottom-0 left-0 right-0 z-[2] mx-[15%] mb-4 flex list-none justify-center p-0 navipos"
    data-te-carousel-indicators>
    <button @click="activeIndex=0"
      type="button"
      data-te-target="#carouselExampleCaptions"
      data-te-slide-to="0"
      data-te-carousel-active
      class="mx-[3px] box-content h-[3px] w-[30px] flex-initial cursor-pointer border-0 border-y-[10px] border-solid border-transparent bg-white bg-clip-padding p-0 -indent-[999px] opacity-50 transition-opacity duration-[600ms] ease-[cubic-bezier(0.25,0.1,0.25,1.0)] motion-reduce:transition-none"
      aria-current="true"
      aria-label="Slide 1"></button>
    <button @click="activeIndex=1"
      type="button"
      data-te-target="#carouselExampleCaptions"
      data-te-slide-to="1"
      class="mx-[3px] box-content h-[3px] w-[30px] flex-initial cursor-pointer border-0 border-y-[10px] border-solid border-transparent bg-white bg-clip-padding p-0 -indent-[999px] opacity-50 transition-opacity duration-[600ms] ease-[cubic-bezier(0.25,0.1,0.25,1.0)] motion-reduce:transition-none"
      aria-label="Slide 2"></button>
    <button @click="activeIndex=2"
      type="button"
      data-te-target="#carouselExampleCaptions"
      data-te-slide-to="2"
      class="mx-[3px] box-content h-[3px] w-[30px] flex-initial cursor-pointer border-0 border-y-[10px] border-solid border-transparent bg-white bg-clip-padding p-0 -indent-[999px] opacity-50 transition-opacity duration-[600ms] ease-[cubic-bezier(0.25,0.1,0.25,1.0)] motion-reduce:transition-none"
      aria-label="Slide 3"></button>
         <button @click="activeIndex=3"
      type="button"
      data-te-target="#carouselExampleCaptions"
      data-te-slide-to="2"
      class="mx-[3px] box-content h-[3px] w-[30px] flex-initial cursor-pointer border-0 border-y-[10px] border-solid border-transparent bg-white bg-clip-padding p-0 -indent-[999px] opacity-50 transition-opacity duration-[600ms] ease-[cubic-bezier(0.25,0.1,0.25,1.0)] motion-reduce:transition-none"
      aria-label="Slide 3"></button>
  </div>
  
</template>

<style scoped>
.prevpos{
  position: relative;
  top:-200px;
  left:-400px
}
.nxtpos{
  position: relative;
  top:-200px;
  left:400px
}

.fade-in {
	opacity: 1;
	animation-name: fadeInOpacity;
	animation-iteration-count: 1;
	animation-timing-function: ease-out;
	animation-duration: 1.7s;
}

@keyframes fadeInOpacity {
	0% {
		opacity: 0.3;
	}
	100% {
		opacity: 1;
	}
}

.tit-font{
  font-size: 25px;
}

.navipos{
  position: relative;
  top:-40px
}
</style>
