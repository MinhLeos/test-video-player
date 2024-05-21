<template>
  <section
    class="xl:px-5 px-0 flex flex-col items-center justify-center my-10"
  >
    <div class="w-full max-w-[1440px] aspect-w-16 aspect-h-9 relative m-auto">
      <div v-if="!isPlayVideo">
        <img
          src="https://drberg-dam.imgix.net/video-thumbnails/10b6b71d-b58f-4b27-8337-d9bc58f53ef8.png"
          alt="embed-thumnail"
          class="mx-auto w-full my-auto object-contain"
          width="1228"
          height="690"
        />
        <button
          aria-label="Play"
          class="absolute top-[35%] 2xl:top-[25%] left-[50%] flex justify-center items-center group rounded-full hover:outline-4 hover:outline hover:outline-offset-8 hover:outline-white focus:!outline focus:!outline-4 focus:!outline-offset-4 focus:!outline-white"
          @click="playMedia"
        >
          <span>
            <span
              class="flex justify-center items-center bg-gray-darkest bg-opacity-30 w-10 h-10 xs:w-14 xs:h-14 sm:w-20 sm:h-20 xmd:w-28 xmd:h-28 bg-transparent"
            >
              <img
                class="w-full"
                src="https://drberg-dam.imgix.net/icons/icon-filled-editing-play2.svg"
                alt="button-play"
                width="128"
                height="128"
                sizes=""
                srcset=""
              />
            </span>
          </span>
        </button>
      </div>
      <div
        v-else
        class="mx-auto w-full h-full my-auto object-contain flex items-center justify-center"
      >
        <mgi-video-player
          v-if="isPlayVideo"
          :isAutoPlay="true"
          :thumnailPreviewUrl="thumnailPreviewUrl"
          :captionUrl="captionUrl"
          :thumnailUrl="thumnailUrl"
          :src="playUrl"
          :thumnailAltText="thumnailAltText"
        ></mgi-video-player>
      </div>
    </div>
    <div class="w-[80%] flex flex-col gap-y-5 mt-5">
      <label class="flex flex-col gap-y-5 items-center mb-10 xsm:mb-0">
        <span class="block min-w-[120px]">Video Url</span>
        <input
          class="block w-full border border-solid px-3 py-1"
          type="text"
          name="url"
          v-model="url"
      /></label>
      <label class="flex flex-col gap-y-5 items-center mb-10 xsm:mb-0">
        <span class="block min-w-[120px]">Video Preview Url</span>
        <input
          class="block w-full border border-solid px-3 py-1"
          type="text"
          name="thumnailPreview"
          v-model="thumnailPreview"
      /></label>
      <label class="flex flex-col gap-y-5 items-center mb-10 xsm:mb-0">
        <span class="block min-w-[120px]">Video Caption Url</span>
        <input
          class="block w-full border border-solid px-3 py-1"
          type="text"
          name="caption"
          v-model="caption"
      /></label>
      <label class="flex flex-col gap-y-5 items-center mb-10 xsm:mb-0">
        <span class="block min-w-[120px]">Video thumnail Url</span>
        <input
          class="block w-full border border-solid px-3 py-1"
          type="text"
          name="thumnail"
          v-model="thumnail"
      /></label>
      <button class="border border-solid w-40 m-auto hover:opacity-70 active:opacity-40" @click="handleClick">Load Video</button>
    </div>
  </section>
</template>

<script setup lang="ts">
const icon = "cat"
const isPlayVideo = ref(false);
const playMedia = () => {
  isPlayVideo.value = !isPlayVideo.value;
};
const playUrl = ref(
  'https://hls.drberg.com/encoded-assets/membership-site-fixed-final/membership-site-fixed-final.m3u8'
);
const url = ref('');
const thumnailPreviewUrl = ref("https://hls.drberg.com/encoded-assets/membership-site-fixed-final/sprite.vtt");
  // 'https://image.mux.com/VZtzUzGRv02OhRnZCxcNg49OilvolTqdnFLEqBsTwaxU/storyboard.vtt';
const captionUrl = ref('https://hls.drberg.com/encoded-assets/membership-site-fixed-final/caption.vtt');
const thumnailUrl = ref('https://hls.drberg.com/encoded-assets/membership-site-fixed-final/thumbnail_main.jpg');
const thumnailAltText = 'Alt Text Demo Thumnail';
const caption = ref('');
const thumnailPreview = ref('');
const thumnail = ref('');
const handleClick = () => {
    if (!url.value?.trim()) {
    alert('nhập url')
    return
  }
  playUrl.value = url.value
  captionUrl.value = caption.value
  thumnailPreviewUrl.value = thumnailPreview.value
  thumnailUrl.value = thumnail.value
}
</script>
<style></style>
