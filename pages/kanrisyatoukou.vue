<template>
    <div>
        <h1 class = " text-black text-[32px]   mt-[30px] h-[50px] text-center border-b-4 font-['Noto Sans']">管理者投稿用</h1>
        <ul class = "py-7">
                <li class="flex items-center mb-4 justify-center">
                    <input id="default-radio-1" type="radio" value="" name="default-radio" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                <label for="default-radio-1" class="ms-2 text-sm font-medium text-black dark:text-text-black">ヒグマ速報</label>
                </li>
                <li class="flex items-center mb-4 justify-center">
                    <input id="default-radio-1" type="radio" value="" name="default-radio" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                    <label for="default-radio-1" class="ms-2 text-sm font-medium text-black dark:text-text-black">事故速報</label>
                </li>
                <li class="flex items-center mb-4 justify-center">
                    <input id="default-radio-1" type="radio" value="" name="default-radio" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                    <label for="default-radio-1" class="ms-2 text-sm font-medium text-black dark:text-text-black">除雪速報</label>
                </li>
                <li class="flex items-center mb-4 justify-center ">
                    <input id="default-radio-1" type="radio" value="" name="default-radio" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                    <label for="default-radio-1" class="ms-2 text-sm font-medium text-text-black dark:text-text-black">不審者速報</label>
                </li>
            </ul>
            <div class="w-full h-[54px] mb-10 bg-[#D9D9D9] flex justify-center">
                <div class = " text-black text-[24px] flex items-center font-['Noto Sans']">・住所を入力
                </div>
            </div>
            <div class="w-full h-[222px]  bg-[#D9D9D9]">
                <img :src="mapSrc" alt="Map" class="w-full h-full object-cover" />
            </div>
            <div class = "flex  justify-center py-8 text-black text-[14px] font-['Noto Sans']">
            ※注意事項を入力
            </div>
            <div class = "flex justify-center ">
                        <button class="bg-[#D9D9D9] font-['Noto Sans'] text-black py-3 px-10 rounded">登録</button>
            </div>

    </div>
</template>

<script setup lang="ts">
definePageMeta({ layout: false })
import { computed } from 'vue';

const props = defineProps({
    latitude: Number,
    longitude: Number
});

const zoom = 15; // ズームレベル

const mapSrc = computed(() => {
    return `https://static-maps.yandex.ru/1.x/?ll=${props.longitude},${props.latitude}&z=${zoom}&size=600,300&l=map&pt=${props.longitude},${props.latitude},pm2rdm&lang=ja_JP`;
});
</script>
