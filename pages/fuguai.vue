<template>
    <div>
        <h1 class = " text-black text-[32px]   mt-[30px] h-[50px] text-center border-b-4 font-['Noto Sans']">不具合報告</h1>
        <div class="grid gap-6 mb-6 md:grid-cols-2 justify-center ">
            <label for="name" class="block  text-sm font-medium text-gray-900 dark:text-white "><div class =" text-black text-[24px] flex justify-center py-10">お名前</div></label>
            <input type="text" id="name" class="bg-gray-50 border  border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-[#D9D9D9] dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="お名前" required />
        </div>
        <div class="grid gap-6 mb-6 md:grid-cols-2 justify-center ">
            <label for="maile" class="block  text-sm font-medium text-gray-900 dark:text-white "><div class =" text-black text-[24px] flex justify-center py-10">メールアドレス（任意）</div></label>
            <input type="text" id="maile" class="bg-gray-50 border  border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-[#D9D9D9] dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="メールアドレス" required />
        </div>
        <div class="grid gap-6 mb-6 md:grid-cols-2 justify-center ">
            <label for="res" class="block  text-sm font-medium text-gray-900 dark:text-white "><div class =" text-black text-[24px] flex justify-center py-10">　　フィードバック詳細　　</div></label>
            <input type="text" id="res" class="bg-gray-50 border  border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-[#D9D9D9] dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="フィードバック" required />
        </div>
        <div class = "flex justify-center py-5">
                        <button class="bg-[#D9D9D9] font-['Noto Sans'] text-black py-3 px-10 rounded">送信</button>
        </div>
    </div>
</template>

<script setup lang="ts">
definePageMeta({ layout: false })
</script>
