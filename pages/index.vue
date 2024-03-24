<template>
  <div class="px-4 py-10 lg:container">
    <iframe
      class="aspect-video w-full"
      :src="videoUrl"
      title="YouTube video player"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      referrerpolicy="strict-origin-when-cross-origin"
      allowfullscreen
    ></iframe>
    <section
      class="my-6 grid grid-cols-3 justify-items-center bg-slate-300 py-10 text-xl font-bold text-white"
    >
      <h3 class="col-span-full mb-10 text-black">選擇語言</h3>
      <button
        @click="changeLanguage('Chinese')"
        class="w-2/4 rounded-lg border-2 bg-slate-800 px-2 py-4"
      >
        Chinese
      </button>
      <button
        @click="changeLanguage('English')"
        class="w-2/4 rounded-lg border-2 bg-slate-800 px-2 py-4"
      >
        English
      </button>
      <button
        @click="changeLanguage('Japanese')"
        class="w-2/4 rounded-lg border-2 bg-slate-800 px-2 py-4"
      >
        Japanese
      </button>
    </section>
    <main class="mb-10 mt-10 bg-slate-300 px-8 py-10">
      <ul
        class="mb-8 flex gap-x-4 text-2xl font-medium text-white"
      >
        <li
          v-for="({ name, value }, i) in foodList"
          :key="`${i}+${name}`"
          class=""
        >
          <button
            @click="selectedFood(value)"
            class="block rounded-full border-2 bg-slate-800 px-6 py-4"
          >
            {{ name }}
          </button>
        </li>
      </ul>
      <div class="w-full bg-slate-400 p-6 text-2xl leading-loose">
        <article>
          {{ articleText }}
        </article>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, watchEffect } from "vue";
const videoUrl = ref(
  "https://www.youtube.com/embed/LU8EwukZVAg?si=2okbrF_rdMOBnWqh",
);
const language = ref("Chinese");
const articleText = ref("");

function selectedFood(value) {
  foodList.value.filter((food) => {
    if (food.value === value) {
        videoUrl.value = food.url;
        articleText.value = food.text;
    }
  });
}

const foodList = ref([
  {
    name: "牛肉麵",
    value: "beefNoodle",
    url: "https://www.youtube.com/embed/LrxVTWhBkj0?si=S_bHhAd2PIPPbHBP",
    text: "臺灣最早出現的牛肉麵以紅燒為主，是受成都川菜「小碗紅湯牛肉」啟發所創新演化而成。該道菜色使用豆瓣醬，口味與高雄岡山的豆瓣醬相似，以蠶豆瓣和辣椒製成。岡山為空軍眷村所在地，而四川正好是空軍在抗戰期間的據點。根據飲食史名家逯耀東教授所考證，台灣所謂「川味牛肉麵」實為台灣起源，為老兵想念家鄉四川口味製作，至於以四川為名，可能是創造者籍貫四川，而非四川原有的料理。台灣牛肉麵融合四川的豆瓣醬、上海本幫菜的紅燒、粵菜的高湯、粵東閩南的酸菜，某些口味包含四川的麻辣、台菜的紅蔥頭、南洋的沙茶等諸多元素，因此臺灣牛肉麵並非某一菜系的延伸，而是多重菜系、口味的混合。現在，台灣牛肉麵已發展成海外華人地區的普遍食物，有不少泡麵如滿漢大餐都是以添加牛肉或牛肉調味料作為號召，尤其是在台灣非常普遍。",
  },
  {
    name: "雞肉飯",
    value: "turkeyRice",
    url: "https://www.youtube.com/embed/LU8EwukZVAg?si=giFHZqyCFPws-lzb",
    text: "",
  },
  {
    name: "小籠包",
    value: "xiaolongbao",
    url: "https://www.youtube.com/embed/J3LgTeCQgpk?si=ENGAiJ51owxJQpIz",
    text: "",
  },
]);

const changeLanguage = (lang) => {
  language.value = lang;
};

watchEffect(() => {
  if (language.value === "Chinese") {
    foodList.value = [
      {
        name: "牛肉麵",
        value: "beefNoodle",
        url: "https://www.youtube.com/embed/LrxVTWhBkj0?si=S_bHhAd2PIPPbHBP",
        text: "臺灣最早出現的牛肉麵以紅燒為主，是受成都川菜「小碗紅湯牛肉」啟發所創新演化而成。該道菜色使用豆瓣醬，口味與高雄岡山的豆瓣醬相似，以蠶豆瓣和辣椒製成。岡山為空軍眷村所在地，而四川正好是空軍在抗戰期間的據點。根據飲食史名家逯耀東教授所考證，台灣所謂「川味牛肉麵」實為台灣起源，為老兵想念家鄉四川口味製作，至於以四川為名，可能是創造者籍貫四川，而非四川原有的料理。台灣牛肉麵融合四川的豆瓣醬、上海本幫菜的紅燒、粵菜的高湯、粵東閩南的酸菜，某些口味包含四川的麻辣、台菜的紅蔥頭、南洋的沙茶等諸多元素，因此臺灣牛肉麵並非某一菜系的延伸，而是多重菜系、口味的混合。現在，台灣牛肉麵已發展成海外華人地區的普遍食物，有不少泡麵如滿漢大餐都是以添加牛肉或牛肉調味料作為號召，尤其是在台灣非常普遍。",
      },
      {
        name: "雞肉飯",
        value: "turkeyRice",
        url: "https://www.youtube.com/embed/LU8EwukZVAg?si=giFHZqyCFPws-lzb",
        text: "",
      },
      {
        name: "小籠包",
        value: "xiaolongbao",
        url: "https://www.youtube.com/embed/J3LgTeCQgpk?si=ENGAiJ51owxJQpIz",
        text: "",
      },
    ];
    
  } else if (language.value === "English") {
    foodList.value = [{
        name: "Beef Noodle",
        value: "beefNoodle",
        url: "https://www.youtube.com/embed/LrxVTWhBkj0?si=S_bHhAd2PIPPbHBP",
        text: "Taiwan's Beef Noodle Soup is a culinary masterpiece with a rich historical background and profound cultural depth. It is an indispensable part of the daily lives of the Taiwanese people and a must-try delicacy for many foreign tourists visiting Taiwan. The allure of Beef Noodle Soup lies in its unique broth flavor, carefully selected ingredients, and diverse cooking methods, all of which together forge its distinctive identity.",
      },
      {
        name: "Turkey Rice",
        value: "turkeyRice",
        url: "https://www.youtube.com/embed/LU8EwukZVAg?si=giFHZqyCFPws-lzb",
        text: "",
      },
      {
        name: "xiaolongbao",
        value: "xiaolongbao",
        url: "https://www.youtube.com/embed/J3LgTeCQgpk?si=ENGAiJ51owxJQpIz",
        text: "",
      },];
  } else if (language.value === "Japanese") {
    foodList.value = [{
        name: "台湾の牛肉麺",
        value: "beefNoodle",
        url: "https://www.youtube.com/embed/LrxVTWhBkj0?si=S_bHhAd2PIPPbHBP",
        text: "台湾の牛肉麺は、豊かな歴史的背景と深い文化的根底を持つ美食です。それは台湾人の日常生活に欠かせないものだけでなく、多くの外国人観光客が台湾を訪れた際に必ず試すべき美食の一つでもあります。牛肉麺の魅力は、その独特のスープの風味、選び抜かれた食材、そして多様な調理方法にあり、これらの要素が合わさって牛肉麺のユニークなアイデンティティを形成しています。",
      },
      {
        name: "雞肉飯",
        value: "turkeyRice",
        url: "https://www.youtube.com/embed/LU8EwukZVAg?si=giFHZqyCFPws-lzb",
        text: "",
      },
      {
        name: "小籠包",
        value: "xiaolongbao",
        url: "https://www.youtube.com/embed/J3LgTeCQgpk?si=ENGAiJ51owxJQpIz",
        text: "",
      },];
  }
  selectedFood("beefNoodle");
});
</script>
<style></style>
