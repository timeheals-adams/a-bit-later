<script setup lang="ts">
// This would normally come from an API/database based on the route param
const route = useRoute()
const animeId = route.params.id

// Mock data - replace with actual API call
const animeData = {
  image: 'https://shikimori.one/uploads/poster/animes/59062/eef2d14872e5da4d578fc662557bba51.jpeg',
  title: 'Провожающая в последний путь Фрирен',
  titleEn: 'Tokidoki Bosotto Russia-go de Dereru Tonari no Aalya-san',
  rating: 9.4,
  genres: ['Демоны', 'Сверхъестественное', 'Сёнэн', 'Фэнтези', 'Школа', 'Экшен'],
  description:
    'Одержав победу над Королём демонов, отряд героя Химмеля вернулся домой. Приключение, растянувшееся на десятилетие, подошло к завершению. Волшебница-эльф Фрирен и её отважные товарищи принесли людям мир и разошлись в разные стороны, чтобы спокойно прожить остаток жизни. Однако не всех членов отряда ждёт одинаковая участь. Для эльфов время течёт иначе, поэтому Фрирен вынужденно становится свидетелем того, как её спутники один за другим постепенно уходят из жизни. Девушка осознала, что годы, проведённые в отряде героя, пронеслись в один миг, как падающая звезда в бескрайнем космосе её жизни, и столкнулась с сожалениями об упущенных возможностях. Сможет ли она смириться со смертью друзей и понять, что значит жизнь для окружающих её людей? Фрирен начинает новое путешествие, чтобы найти ответ.',
  nextEpisode: {
    date: '21 авг. 2024 ср 17:30',
    episode: 8,
  },
}

const animeInfo = [
  { label: 'Тип', value: 'ТВ Сериал' },
  { label: 'Эпизодов', value: '7 / 12' },
  { label: 'Статус', value: 'Вышел' },
  { label: 'Ограничения', value: '16+' },
  { label: 'Студия', value: 'Dogakobo' },
  { label: 'Выпуск', value: 'с 3 июля 2024' },
  { label: 'Длительность', value: '24 мин. / серия' },
  { label: 'Снят по манге', value: 'Магическая битва' },
]

const screenshots = [
  'https://shikimori.one/system/screenshots/original/7e3f9d2eecfcac3c770b7d01346408765c17cae7.jpg?1751821137',
  'https://shikimori.one/system/screenshots/original/d289a52537db69572cdce6c7f0584412ce127994.jpg?1751821142',
  'https://shikimori.one/system/screenshots/original/7d286b5a86f6e1203f8355a3726fa5bb6ad6ddf6.jpg?1751821148',
  'https://shikimori.one/system/screenshots/original/5ddbf2b7fe3a06a0187a465f0008c5a0ee0fbcf3.jpg?1751821155',
  'https://shikimori.one/system/screenshots/original/e9558402648ab5e04a8ccdb52e4940fc4d585b22.jpg?1751821162',
]

// Set page meta
useHead({
  title: `${animeData.title} - Anisign`,
  meta: [
    {
      name: 'description',
      content: animeData.description.slice(0, 160) + '...',
    },
  ],
})
</script>

<template>
  <div class="bg-[#0c0c0c] min-h-screen relative">

    <!-- Layout components -->
    <LayoutReport />
    <LayoutHeader />

    <!-- Main content -->
    <div class="px-5">
      <!-- Hero section -->
      <div class="container mt-[100px] sm:mt-[120px] lg:mt-[148px]">
        <div class="flex flex-col lg:flex-row items-start justify-between gap-5 lg:gap-8">
          <!-- Left side: Poster + Main content -->
          <AnimeHero
            :image="animeData.image"
            :title="animeData.title"
            :title-en="animeData.titleEn"
            :rating="animeData.rating"
            :genres="animeData.genres"
            :description="animeData.description"
            :next-episode="animeData.nextEpisode"
          />

          <!-- Divider (desktop only) -->
          <div class="hidden lg:block bg-white h-[624px] opacity-5 w-px"></div>

          <!-- Right side: Info panel -->
          <div class="w-full lg:w-auto">
            <AnimeInfo :info="animeInfo" />
          </div>
        </div>
      </div>

      <!-- Screenshots section -->
      <div class="mt-[80px] sm:mt-[120px] lg:mt-[150px] container">
        <AnimeScreenshots :screenshots="screenshots" />
      </div>
    </div>

    <!-- Footer -->
    <div class="mt-[50px] sm:mt-[75px] lg:mt-[100px]">
      <LayoutFooter />
    </div>
  </div>
</template>
