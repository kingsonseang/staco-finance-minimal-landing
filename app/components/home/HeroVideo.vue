<script setup>
const play = ref(false);

function setPlay() {
    play.value = true;
}

function setPause() {
    play.value = false;
}
</script>

<template>
    <div
        class="max-w-[470px] h-[340px] rounded-[30px] flex overflow-hidden relative after:absolute after:left-0 after:right-0 after:bottom-0 after:top-0 after:z-1 after:bg-gradient-to-br after:from-[117.62deg] after:from-black/50 after:to-black/0">
        <video id="w-full h-full object-cover flex-1" loop autoplay playsinline preload="auto" v-on:play="setPlay"
            v-on:pause="setPause">
            <source src="https://staco-react.vercel.app/assets/h6-video-DaLtBHE1.mp4" type="video/mp4">Your browser does
            not support the video tag.
        </video>
        <UButton :icon="play ? 'i-heroicons-pause' : 'i-heroicons-play'" size="lg"
            @click="play ? video.pause() : video.play()"
            class="absolute bottom-8 right-8 z-5 bg-white rounded-full p-4 text-primary hover:bg-white" />
    </div>
</template>