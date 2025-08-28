<template>
  <div class="container">
    <div class="card" id="card1">
      <span class="icon material-icons">fiber_manual_record</span>
      <div class="number" id="number1">230,432</div>
      <div class="message">ออนไลน์</div>
    </div>
    <div class="card" id="card2">
      <span class="icon material-icons">emoji_events</span>
      <div class="number" id="number2">3,641</div>
      <div class="message">ผู้ชนะวันนี้1111</div>
    </div>
    <div class="card" id="card3">
      <span class="icon material-icons">attach_money</span>
      <div class="number" id="number3">20,150,000</div>
      <div class="message">รางวัลวันนี้</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "StatsCards",
  mounted() {
    const cards = this.$el.querySelectorAll(".card");

    const configs = [
      { id: "number1", type: "online" },
      { id: "number2", type: "winner" },
      { id: "number3", type: "prize" }
    ];

    function generatePositiveRandom(currentValue, type) {
      let delta = 0;
      if (type === "online") {
        delta = Math.floor(currentValue * (Math.random() * 0.02 + 0.01));
      } else if (type === "winner") {
        delta = Math.floor(currentValue * (Math.random() * 0.02 + 0.01));
        if (delta < 1) delta = 1;
      } else if (type === "prize") {
        delta = Math.floor(currentValue * (Math.random() * 0.02 + 0.01));
      }
      return currentValue + delta;
    }

    function animateNumber(elementId, startValue, endValue, callback) {
      let currentValue = startValue;
      const step = Math.max(1, Math.ceil((endValue - startValue) / 20));
      const element = document.getElementById(elementId);

      const interval = setInterval(() => {
        currentValue += step;
        if (currentValue >= endValue) {
          clearInterval(interval);
          currentValue = endValue;
          if (callback) callback();
        }
        element.textContent = currentValue.toLocaleString();
      }, 20);
    }

    function focusRandomCards() {
      cards.forEach(card => card.classList.remove("active"));

      const count = Math.floor(Math.random() * 3) + 1;
      const shuffled = [0, 1, 2].sort(() => 0.5 - Math.random());
      const selectedIndexes = shuffled.slice(0, count);

      selectedIndexes.forEach(index => {
        const card = cards[index];
        card.classList.add("active");

        const { id, type } = configs[index];
        const numberEl = document.getElementById(id);
        const currentValue = parseInt(numberEl.textContent.replace(/,/g, ""));
        const newValue = generatePositiveRandom(currentValue, type);

        animateNumber(id, currentValue, newValue);
      });

      setTimeout(focusRandomCards, 3000);
    }

    focusRandomCards();
  }
};
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  background-color: #111;
  margin: 0;
  padding: 0;
}

.container {
  width: 100%;
  max-width: 600px;
  display: flex;
  justify-content: space-between;
  gap: 10px;
  padding: 10px;
  box-sizing: border-box;
}

.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
  padding: 10px;
  background-color: #122229;
  border-radius: 12px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  color: white;
  backdrop-filter: blur(6px);
  min-width: 0;
  transition: border 0.2s, box-shadow 0.2s;
  border: 1px solid #FFD700;
}

.card.active {
  box-shadow: 0 0 8px 2px rgba(255, 215, 0, 0.8);
}

.icon {
  font-size: 22px;
  color: #FFD700;
}

.number {
  font-size: 1em;
  font-weight: bold;
  margin: 6px 0;
  color: white;
}

.message {
  font-size: 0.85em;
  color: rgba(255, 255, 255, 0.6);
}
</style>
