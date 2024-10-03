<template>
  <div class="overlay" v-if="isOpen">
    <div class="card">
      <button class="close-button" @click="closeCard">×</button>
      <img class="profile-image"  alt="Profile Image" />
      <div class="card-content">
        <h2>Владимир Соловьёв</h2>
        <p>По будням в 23:20 и по воскресеньям в 23:40 в телепрограмме «Воскресный вечер».</p>
        <p>
          «На станции замер сгусток программы дня (прим.), непредвиденные вещи, которым можно
          придавать актуальное или другое значение. Потом поместите запись программы на «Тот
          день в истории России».
        </p>
        <p>
          За программу "Вечер с Владимиром Соловьёвым" ведущий награждён премией "ТЭФИ".
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProfileCard",
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    closeCard() {
      this.isOpen = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(217, 217, 217, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  backdrop-filter: blur(24px)
}

.card {
  background-color: white;
  border-radius: 10px;
  width: 400px;
  padding: 20px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.profile-image {
  border-radius: 50%;
  width: 80px;
  height: 80px;
  object-fit: cover;
}

.card-content {
  margin-top: 20px;
  text-align: center;

  h2 {
    font-size: 20px;
    margin-bottom: 10px;
  }

  p {
    font-size: 14px;
    margin-bottom: 10px;
    line-height: 1.5;
  }
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
}

.close-button:hover {
  color: #f00;
}
</style>
