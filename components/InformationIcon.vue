<template>
    <div class="flex">
        <!-- 画面情報表示部分 -->
        <div class="w-full flex mt-4 mb-7 ml-2 mr-2 items-center justify-center">
            <img
            :src="iconSrc"
            class="w-17 h-16 w-max-[67px] h-max-[67px] p-1 mr-3"
            :alt="iconAlt"

            />
            <h1 :class="textColorClass" class="text-5xl font-bold font-['Noto Sans']">
            {{ textDetailPages }}
            </h1>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { useRoute } from 'vue-router';

// 画像をインポート
import higumaIcon from '@/assets/img/higumaImg/higumaIcon.png';
import jikoIcon from '@/assets/img/jikoImg/jikoIcon.png';
import josetsuIcon from '@/assets/img/josetsuImg/josetsuIcon.png';
import fusinshaIcon from '@/assets/img/fusinshaImg/fusinshaIcon.png';

const route = useRoute();

const iconSrc = computed(() => {
    if (route.path.includes('higuma')) {
        return higumaIcon;
    } else if (route.path.includes('jiko')) {
        return jikoIcon;
    } else if (route.path.includes('josetsu')) {
        return josetsuIcon;
    } else if (route.path.includes('fusinsha')) {
        return fusinshaIcon;
    }
    return '';
});

const iconAlt = computed(() => {
    if (route.path.includes('higuma')) {
        return 'ヒグマアイコン';
    } else if (route.path.includes('jiko')) {
        return '事故アイコン';
    } else if (route.path.includes('josetsu')) {
        return '除雪アイコン';
    } else if (route.path.includes('fusinsha')) {
        return '不審者アイコン';
    }
    return '';
});

const textDetailPages = computed(() => {
    if (route.path.includes('higuma')) {
        return 'ヒグマ速報';
    } else if (route.path.includes('jiko')) {
        return '事故速報';
    } else if (route.path.includes('josetsu')) {
        return '除雪速報';
    } else if (route.path.includes('fusinsha')) {
        return '不審者速報';
    }
    return '';
});

const textColorClass = computed(() => {
    if (route.path.includes('higuma')) {
        return 'text-[#ff3e3e]';
    } else if (route.path.includes('jiko')) {
        return 'text-[#ffa629]';
    } else if (route.path.includes('josetsu')) {
        return 'text-[#578cff]';
    } else if (route.path.includes('fusinsha')) {
        return 'text-[#4f4f4f]';
    }
    return '';
});
</script>