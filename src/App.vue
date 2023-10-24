<script>
export default {
  data() {
    return {
      days: null,
      hours: null,
      minutes: null,
      seconds: null,
      targetDate: new Date(2028, 9, 30), // 30 Ekim 2028 (Ay - 1 şeklinde, yani Ekim ayı 9 olacak)
      showMessage: false,
      message: "2028 yılına 30 Ekim'e ulaşıldı!"
    };
  },
  mounted() {
    setInterval(() => {
      const now = new Date();
      const timeDifference = this.targetDate - now;

      this.days = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
      this.hours = Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      this.minutes = Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60));
      this.seconds = Math.floor((timeDifference % (1000 * 60)) / 1000);

      if (timeDifference <= 0) {
        this.showMessage = true;
      }
    }, 1000);
  }
};
</script>

<template>
  <div class="flex flex-col items-center justify-center h-screen">
    <div class="text-4xl font-bold mb-4">
      {{ days }} gün {{ hours }} saat {{ minutes }} dakika {{ seconds }} saniye
    </div>
    <div v-if="showMessage" class="text-lg">{{ message }}</div>
  </div>
</template>

<style>
body {
  font-family: 'Arial', sans-serif;
}
</style>
