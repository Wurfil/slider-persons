<template>
  <div class="slider-container">
      <div class="slider">
        <ButtonScroll direction="left" class="button-prev"/>
        <PersonItem
            v-for="(person, index) in persons.slice(start,end)"
            :key="'main-' + index"
            :image="person.image"
            :name="person.name"
            class="slider-item"
        />
        <ButtonScroll direction="right" class="button-next"/>
      </div>
      </div>
  <ProfileCard/>
</template>


<script setup>
import { ref, computed } from 'vue';
import ProfileCard from "../UI/Card.vue";
import PersonItem from "../UI/PersonItem.vue";
import ButtonScroll from "../UI/ButtonScroll.vue";

const image = 'https://cdn-st3.smotrim.ru/vh/pictures/bq/524/810/6.jpg';
const persons = [
  { name: '1Игорь Кожевин', image },
  { name: '2Дмитрий Киселёв', image },
  { name: '3Эрнест Мацкявичюс', image },
  { name: '4Ольга Скабеева', image },
  { name: '5Владимир Соловьёв', image },
  { name: '6Евгений Попов', image },
  { name: '7Эрнест Мацкявичюс', image },
  { name: '8Игорь Кожевин', image },
  { name: '9Дмитрий Киселёв', image },
  { name: '10Эрнест Мацкявичюс', image },
  { name: '11льга Скабеева', image },
  { name: '12ладимир Соловьёв', image },
  { name: '13Евгений Попов', image },
  { name: '14Эрнест Мацкявичюс', image },
  { name: '15Игорь Кожевин', image },
  { name: '16Дмитрий Киселёв', image },
  { name: '17Эрнест Мацкявичюс', image },
  { name: '18Ольга Скабеева', image },
  { name: '19Владимир Соловьёв', image },
  { name: '20Евгений Попов', image },
  { name: '21Эрнест Мацкявичюс', image },
];
const itemsPerSlide = 8; // Количество видимых элементов

const start = ref(0)
const end = ref(8)

const totalItems = persons.length;

const currentIndex = ref(itemsPerSlide); // Начинаем со смещением
const isTransitioning = ref(false);

// Клонируем последние и первые элементы
const clonedEndItems = computed(() => persons.slice(-itemsPerSlide));
const clonedStartItems = computed(() => persons.slice(0, itemsPerSlide));

const totalCarouselItems = computed(() => {
  return [
    ...clonedEndItems.value,
    ...persons,
    ...clonedStartItems.value,
  ];
});


function nextSlide() {
  if (!isTransitioning.value) {
    isTransitioning.value = true;
    currentIndex.value += 1;
  }
}

function prevSlide() {
  if (!isTransitioning.value) {
    isTransitioning.value = true;
    currentIndex.value -= 1;
  }
}

function handleTransitionEnd() {
  isTransitioning.value = false;

  // Проверяем, если мы на клонированных элементах, и перемещаемся без анимации
  if (currentIndex.value >= totalItems + itemsPerSlide) {
    currentIndex.value = itemsPerSlide;
    isTransitioning.value = false;
  } else if (currentIndex.value <= 0) {
    currentIndex.value = totalItems;
    isTransitioning.value = false;
  }
}
</script>


<style scoped lang="scss">
.slider-container {
  display: flex;
  justify-content: center;
  width: 100vw;
  align-items: center;
  .slider {
    display: flex;
    position: relative;
    justify-content: center;
    align-items: center;
  }

  button {
    position: absolute;
    top: 25%;
    &.button-next{
      right: -12px;

    }
    &.button-prev{
    left: -12px;
    }
  }
}



.slider-track {
  display: flex;
  transition: transform 0.5s ease-in-out;
}

.slider-container button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}

</style>
