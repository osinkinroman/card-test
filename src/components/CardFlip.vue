<script setup lang="ts">
import { ref } from 'vue';

const isFlipped = ref(false);
const isMovedUp = ref(false);

const flipAndMoveCard = () => {
    isFlipped.value = true;

    setTimeout(() => {
        isMovedUp.value = true;
    }, 600);
};
</script>

<template>
    <div class="flex flex-col items-center justify-center h-screen bg-gray-100">
        <div class="flex space-x-4 mt-40">
            <div class="card-container">
                <div class="card">
                    <div class="card-face card-back" />
                </div>
            </div>
            <div class="card-container" :class="{ 'move-up': isMovedUp }">
                <div class="card" :class="{ 'flipped': isFlipped }">
                    <div class="card-face card-front" />
                    <div class="card-face card-back" />
                </div>
            </div>
            <div class="card-container">
                <div class="card">
                    <div class="card-face card-back" />
                </div>
            </div>
        </div>
        <button class="mt-8 px-6 py-2 bg-blue-600 text-white rounded hover:bg-blue-700 transition duration-300"
            @click="flipAndMoveCard">Flip Card</button>
    </div>
</template>
  
<style scoped>
.card-container {
    transition: transform 0.6s;
}

.card {
    width: 100px;
    height: 150px;
    transform-style: preserve-3d;
    transition: transform 0.6s;
    cursor: pointer;
}

.card-face {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    background-size: cover;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.card-front {
    width: 100%;
    height: 100%;
    background-image: url('../public/card.svg');
    transform: rotateY(180deg);

}

.card-back {
    background-image: url('../public/back.svg');
    background-size: cover;

}

.flipped {
    transform: rotateY(180deg);
}

.move-up {
    transform: translateY(-200px);
    transition-delay: 0.6s;
}

@media (max-width: 280px) {

    .card {
        width: 56px;
        height: 83px;
    }

    .move-up {
        transform: translateY(-100px);
    }
}

@media (min-width: 281px) and (max-width: 600px) {

    .card {
        width: 93px;
        height: 138px;
    }

    .move-up {
        transform: translateY(-150px);
    }
}

@media (min-width: 601px) and (max-width: 1024px) {


    .card {
        width: 130px;
        height: 193px;
    }

    .move-up {
        transform: translateY(-180px);
    }
}

@media (min-width: 1025px) {
    .card {
        width: 185px;
        height: 276px;
    }

    .move-up {
        transform: translateY(-300px);
    }
}
</style>
  