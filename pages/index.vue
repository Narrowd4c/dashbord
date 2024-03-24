<template>
  <div class="px-4 py-10 lg:container">
    <iframe class="w-full aspect-video" src="https://www.youtube.com/embed/LrxVTWhBkj0?si=S_bHhAd2PIPPbHBP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    <section class="bg-slate-300 my-6 py-10 grid grid-cols-3 justify-items-center font-bold text-xl text-white">
      <h3 class="col-span-full mb-10 text-black">選擇語言</h3>
      <button class="w-2/4 rounded-lg border-2 px-2 py-4 bg-slate-800">Chinese</button>
      <button class="w-2/4 rounded-lg border-2 px-2 py-4 bg-slate-800">English</button>
      <button class="w-2/4 rounded-lg border-2 px-2 py-4 bg-slate-800">Japanese</button>
    </section>
    <main class="bg-slate-300 py-10 mt-10 mb-10 px-8">
        <ul class="grid grid-rows-1 grid-cols-5 mb-8 font-medium text-4xl text-white">
            <li v-for="({name}, i) in foodList" :key="`${i}+${name}`" class=""><button class="block rounded-full border-2 px-6 py-4 bg-slate-800">{{ name }}</button></li>
        </ul>
        <div class="bg-slate-400 w-full text-2xl leading-loose p-6">
            <h2>介紹</h2>
            <article>
                臺灣最早出現的牛肉麵以紅燒為主，是受成都川菜「小碗紅湯牛肉」啟發所創新演化而成。該道菜色使用豆瓣醬，口味與高雄岡山的豆瓣醬相似，以蠶豆瓣和辣椒製成。岡山為空軍眷村所在地，而四川正好是空軍在抗戰期間的據點。根據飲食史名家逯耀東教授所考證，台灣所謂「川味牛肉麵」實為台灣起源，為老兵想念家鄉四川口味製作，至於以四川為名，可能是創造者籍貫四川，而非四川原有的料理。
台灣牛肉麵融合四川的豆瓣醬、上海本幫菜的紅燒、粵菜的高湯、粵東閩南的酸菜，某些口味包含四川的麻辣、台菜的紅蔥頭、南洋的沙茶等諸多元素，因此臺灣牛肉麵並非某一菜系的延伸，而是多重菜系、口味的混合。現在，台灣牛肉麵已發展成海外華人地區的普遍食物，有不少泡麵如滿漢大餐都是以添加牛肉或牛肉調味料作為號召，尤其是在台灣非常普遍。</article>
        </div>
    </main>
  </div>

</template>

<script setup lang="ts">
import { ref } from "vue";
type Food = {
  name: string;
  value: string;
};

const foodList = ref<Array<Food>>([
  { name: "牛肉麵", value: '' },
  { name: "雞肉飯", value: '' },
  { name: "小籠包", value: '' },
]);
</script>
<style></style>
