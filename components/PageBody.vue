<template>
    <div class="flex flex-col items-center">
        <!-- ページ表示フレーム部-->
        <div class="h-auto mb-10 flex-col justify-start items-center gap-[20px] inline-flex sm:h-auto sm:gap-[20px] w-full">
            <div v-for="(group, index) in groupedDataList" :key="index" class="w-full">
                <div @click="toggle(index)" class="cursor-pointer bg-gray-200 p-4 w-full text-center text-[32px] text-bold">
                    {{ group.date }}
                </div>
                <div v-if="isOpen(index)" class="w-full">
                    <div v-for="(data, dataIndex) in group.items" :key="dataIndex">
                        <!-- 各種速報情報表示部分 -->
                        <!-- 地域 -->
                        <AreaNameDisplay class="mb-5 mt-5" :area="data.area" />

                        <!-- 地図情報 -->
                        <AreaMapDisplay class="mb-5 mt-5" :latitude="data.latitude" :longitude="data.longitude" />

                        <!-- 注意情報 -->
                        <CoutionaryInformationDisplay v-for="(info, infoIndex) in data.information" :key="infoIndex" :info="info" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
//import CoutionaryInformationDisplay from './CoutionaryInformationDisplay.vue';

//テストデータ 仕様は後ほど変更(データをデータベースから持ってくるようにする)
//コンポーネントは切り分ける予定
const dataList = ref([
    {
        date: '2024年10月24日',
        area: '稚内市富岡一丁目2290-28',
        latitude: 45.4152,
        longitude: 141.6734,
        information: [
            '※付近に近づかないようにしてください',
            '※また生ごみなど野外に放置しないでください'
        ]
    },
    {
        date: '2024年10月25日',
        area: '札幌市中央区北1条西2丁目',
        latitude: 43.06417,
        longitude: 141.34694,
        information: [
            '※注意情報1',
            '※注意情報2'
        ]
    },
    {
        date: '2024年10月26日',
        area: 'ダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータ',
        latitude: 20.212630,
        longitude: -89.106929,
        information: [
            'ダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータ',
            'ダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータダミーデータ'
        ]
    },
    {
        date: '2024年10月24日',
        area: '稚内市富岡一丁目2290-28',
        latitude: 45.4152,
        longitude: 141.6734,
        information: [
            '※付近に近づかないようにしてください',
            '※また生ごみなど野外に放置しないでください'
        ]
    },
]);


// 速報情報を日付ごとにグループ化
// new Date(a.date).getTime() - new Date(a.date).getTime()で日付の昇順に並び替え
const groupedDataList = computed(() => {
    const grouped = dataList.value.reduce((acc: { [key: string]: typeof dataList.value }, data) => {
        const date = data.date;
        if (!acc[date]) {
            acc[date] = [];
        }
        acc[date].push(data);
        return acc;
    }, {});

    return Object.keys(grouped).map(date => ({
        date,
        items: grouped[date]
    })).sort((a, b) => new Date(a.date).getTime() - new Date(b.date).getTime());
});

const openIndices = ref<number[]>([0]); // 初期状態で最新の日付を開いた状態にする

const toggle = (index: number) => {
    if (openIndices.value.includes(index)) {
        openIndices.value = openIndices.value.filter(i => i !== index);
    } else {
        openIndices.value.push(index);
    }
};

const isOpen = (index: number) => {
    return openIndices.value.includes(index);
};
</script>
