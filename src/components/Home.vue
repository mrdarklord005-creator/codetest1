<template>
  <div class="container-home">
    <img class="img-logo" :src="require('@/assets/mercy-logo-f.png')" alt="Background Image"/>
    <div>    
      <span class="text1">เว็บตรงแท้ อันดับ 1</span>
      <br><b class="text2">✨การันตีผู้ใช้งานจริงนับล้านยูสเซอร์ ลูกค้าใหม่ เพิ่มอัตราการชนะ ทันที !!</b>
    </div>
    <div class="button-container">
    <a href="https://lin.ee/knMX628" class="custom-button1">
        <i class="fas fa-user-plus"></i>  <!-- ไอคอนสมัครสมาชิก -->
        สมัครสมาชิก
    </a>
    <a href="https://lin.ee/knMX628" class="custom-button2">
        <i class="fas fa-comments"></i>  <!-- ไอคอนติดต่อแอดมิน -->
        ติดต่อแอดมิน
    </a>
</div>

    <div class="online-all">
  <div class="user-online-status">
    <i class="fas fa-circle online-icon"></i>
    <span class="online-count">ออนไลน์ <span class="online-num" ref="onlineCountAll">{{ onlineCountAll }}</span> คน</span>
  </div>
</div>
    <div class="rank-payment">
        <span class="text3">🏆 อันดับการถอน</span>
    </div> 
    <div class="container2" id="container">
    <!-- การ์ดจะถูกเพิ่มที่นี่โดย JavaScript -->
  </div>
        <span class="text4">🔥 เปอร์เซ็นต์เกมแตกสูง</span>
        <div class="card-container">
    <!-- Card 1 -->
    <div class="card">
      <a href="https://lin.ee/knMX628">
        <div class="card-description">
          <img class="img-game1"/>
          <!-- เพิ่มข้อความ "มาแรง" ที่มุมขวาบน -->
          <div class="badge">HOT</div>
          <div class="chance-status"><b>🔥โอกาส 87.68%</b></div>
          <div class="online-status"><b ref="onlineCount1">🟢ออนไลน์ {{ onlineCount1 }}</b></div>
        </div>
    </a>
  </div>
    
    <div class="card">
      <a href="https://lin.ee/knMX628">
        <div class="card-description">
          <img class="img-game2"/>
          <div class="badge">HOT</div>
          <div class="chance-status"><b>🔥โอกาส 91.05%</b></div>
        <div class="online-status"><b ref="onlineCount2">🟢ออนไลน์ {{ onlineCount2 }}</b></div>
        </div>
      </a>
    </div>

    <div class="card">
      <a href="https://lin.ee/knMX628">
        <div class="card-description">
          <img class="img-game3" />
          <div class="badge">HOT</div>
          <div class="chance-status"><b>🔥โอกาส 89.68%</b></div>
        <div class="online-status"><b ref="onlineCount3">🟢ออนไลน์ {{ onlineCount3 }}</b></div>
        </div>
      </a>
    </div>

    <div class="card">
      <a href="https://lin.ee/knMX628">
        <div class="card-description">
          <img class="img-game4"/>
          <div class="badge">HOT</div>
          <div class="chance-status"><b>🔥โอกาส 85.56%</b></div>
        <div class="online-status"><b ref="onlineCount4">🟢ออนไลน์ {{ onlineCount4 }}</b></div>
        </div>
      </a>
    </div>

    <div class="card">
      <a href="https://lin.ee/knMX628">
        <div class="card-description">
          <img class="img-game5"/>
          <div class="badge">HOT</div>
          <div class="chance-status"><b>🔥โอกาส 92.11%</b></div>
        <div class="online-status"><b ref="onlineCount5">🟢ออนไลน์ {{ onlineCount5 }}</b></div>
        </div>
        </a>
    </div>

    <div class="card">
      <a href="https://lin.ee/knMX628">
        <div class="card-description">
          <img class="img-game6" />
          <div class="badge">HOT</div>
          <div class="chance-status"><b>🔥โอกาส 90.18%</b></div>
        <div class="online-status"><b ref="onlineCount6">🟢ออนไลน์ {{ onlineCount6 }}</b></div>
        </div>
      </a>
    </div>
  </div>

  <div class="slider-container">
    <div class="slider" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
      <div v-for="(slide, index) in slides" :key="index" class="slide">
        <img :src="require(`@/assets/${slide.src}`)" :alt="slide.alt" />
      </div>
    </div>
    <!-- Golden Dots -->
    <div class="dots-container">
      <div
        v-for="(slide, index) in slides"
        :key="index"
        :class="['dot', { active: currentIndex === index }]"
        @click="goToSlide(index)"
      ></div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "StatsCards",
  data() {
    return {
      currentIndex: 0,
      onlineCount1: "958",
      onlineCount2: "2,348",
      onlineCount3: "1,125",
      onlineCount4: "893",
      onlineCount5: "3,250",
      onlineCount6: "1,112",
      onlineCountAll: "189,631",
      slides: [
        { src: 'photo_6228624588875613744_y.jpg', alt: 'Image 1' },
        { src: 'photo_6228624588875613745_y.jpg', alt: 'Image 2' },
        { src: 'certi.jpg', alt: 'Image 3' }
      ]
    };
  },
  methods: {
     animateNumber(refName, startValue, endValue, callback) {
      let currentValue = startValue;
      const step = Math.max(1, Math.ceil((endValue - startValue) / 20));

      // ใช้ Vue.nextTick เพื่อให้มั่นใจว่า DOM ถูกเรนเดอร์แล้ว
      this.$nextTick(() => {
        const element = this.$refs[refName];

        if (element) {
          const interval = setInterval(() => {
            currentValue += step;
            if (currentValue >= endValue) {
              clearInterval(interval);
              currentValue = endValue;
              if (callback) callback();
            }
            element.textContent = currentValue.toLocaleString();
          }, 100);
        }
      });
    },
    updateOnlineCount() {
      setInterval(() => {
        // แปลงค่ากลับเป็นตัวเลขก่อน
        let count1 = parseInt(this.onlineCount1.replace(/,/g, '')) || 0;
        let count2 = parseInt(this.onlineCount2.replace(/,/g, '')) || 0;
        let count3 = parseInt(this.onlineCount3.replace(/,/g, '')) || 0;
        let count4 = parseInt(this.onlineCount4.replace(/,/g, '')) || 0;
        let count5 = parseInt(this.onlineCount5.replace(/,/g, '')) || 0;
        let count6 = parseInt(this.onlineCount6.replace(/,/g, '')) || 0;
        let countAll = parseInt(this.onlineCountAll.replace(/,/g, '')) || 0;

        // สุ่มตัวเลขเพิ่มหรือลบ
        const randomChange = Math.random() > 0.5 ? 1 : -1;
        count1 += randomChange * Math.floor(Math.random() * 10);
        count2 += randomChange * Math.floor(Math.random() * 10);
        count3 += randomChange * Math.floor(Math.random() * 10);
        count4 += randomChange * Math.floor(Math.random() * 10);
        count5 += randomChange * Math.floor(Math.random() * 10);
        count6 += randomChange * Math.floor(Math.random() * 10);
        countAll += randomChange * Math.floor(Math.random() * 10);

        
        // ใช้ animateNumber เพื่ออัปเดตค่าตัวเลข
        this.onlineCount1 = count1.toLocaleString();
        this.onlineCount2 = count2.toLocaleString();
        this.onlineCount3 = count3.toLocaleString();
        this.onlineCount4 = count4.toLocaleString();
        this.onlineCount5 = count5.toLocaleString();
        this.onlineCount6 = count6.toLocaleString();

        this.animateNumber('onlineCountAll', parseInt(this.onlineCountAll.replace(/,/g, '')) || 0, countAll, () => {
          this.onlineCountAll = countAll.toLocaleString();
        });


    }, 3000); // อัปเดตทุกๆ 3 วินาที
  },
    nextSlide() {
    if (this.slides && this.slides.length > 0) {  // ตรวจสอบว่า slides ไม่เป็น undefined และมีค่า
      this.currentIndex = (this.currentIndex + 1) % this.slides.length;
    }
  },
  prevSlide() {
    if (this.slides && this.slides.length > 0) {  // ตรวจสอบว่า slides ไม่เป็น undefined และมีค่า
      this.currentIndex = (this.currentIndex - 1 + this.slides.length) % this.slides.length;
    }
  },
  goToSlide(index) {
    if (this.slides && this.slides.length > 0) {  // ตรวจสอบว่า slides ไม่เป็น undefined และมีค่า
      this.currentIndex = index;
    }
  }
  },
  mounted() {
    this.updateOnlineCount();

    const bankLogos = [
      "BAAC.png", "BAY.png", "BBL.png", 
      "GSB.png", "KBANK.png", 
      "KTB.png", "PromptPay.png", "SCB.png", 
      "TTB.png", "TrueMoney.png", "UOB.png"
    ];

    function generateRandomData() {
      const amounts = ["1,000", "2,000", "5,000", "6,000", "7,000", "8,000", "15,000", "1,500", "1,300", "1,800", "20,000", "15,000", "29,000", "3,320", "15,000", "15,000", "3,200", "2,300", "11,100", "13,000", "35,000", "50,800", "20,200", "31,100", "22,200", "12,300", "1,100"];
      const randomAmountIndex = Math.floor(Math.random() * amounts.length);
      const randomBankIndex = Math.floor(Math.random() * bankLogos.length);
      const randomDigits = Math.floor(Math.random() * 100).toString().padStart(2, '0');
      const randomChar = String.fromCharCode(Math.floor(Math.random() * 26) + 97);
      const user = `rosa${randomChar}${randomDigits}xx`;

      const now = new Date();

      // อาร์เรย์ของชื่อเดือนภาษาไทย
      const months = [
        'ม.ค.', 'ก.พ.', 'มี.ค.', 'เม.ย.', 'พ.ค.', 'มิ.ย.',
        'ก.ค.', 'ส.ค.', 'ก.ย.', 'ต.ค.', 'พ.ย.', 'ธ.ค.'
      ];

      // รูปแบบวันที่ที่ต้องการ
      const day = now.getDate().toString().padStart(2, '0'); // วันที่
      const month = months[now.getMonth()]; // ชื่อเดือนภาษาไทย
      const year = (now.getFullYear() + 543); // ปีพุทธศักราช (บวก 543 เพื่อให้ได้ปี พ.ศ.)
      const hours = now.getHours().toString().padStart(2, '0'); // ชั่วโมง
      const minutes = now.getMinutes().toString().padStart(2, '0'); // นาที
      const seconds = now.getSeconds().toString().padStart(2, '0'); // วินาที

      const timestamp = `${day} ${month} ${year} ${hours}:${minutes}:${seconds}`; // ผลลัพธ์สุดท้าย

      return {
        user: user,
        amount: amounts[randomAmountIndex],
        timestamp: timestamp,
        bankLogo: bankLogos[randomBankIndex]
      };
    }

    function addCard(isLatest = true) {
      const data = generateRandomData();
      const container = document.getElementById("container");

      const card = document.createElement("div");
      card.classList.add("card-two");

      const speedClasses = ['speed1', 'speed2', 'speed3'];
      const randomSpeedClass = speedClasses[Math.floor(Math.random() * speedClasses.length)];
      card.classList.add(randomSpeedClass);

      card.innerHTML = `
        <div class="card-left">
          <div class="logo-section">
            <img src="https://raw.githubusercontent.com/casperstack/thai-banks-logo/refs/heads/master/icons/${data.bankLogo}" alt="${data.bankLogo}" style="width: 40px; height: auto;">
          </div>
          <div class="info-section">
            <div class="user-info">ยูส: <span class="amount">${data.user} </span></div>
            <div class="transaction-info">ยอดถอน: <span class="amount">${data.amount} </span>บาท</div>
            <div class="transaction-info">เวลา: <span class="amount">${data.timestamp} </span></div>
          </div>
        </div>
        <div class="card-right">
          <div id="status-icon" class="loading-icon"></div>
          <div id="check-icon" class="check-icon material-icons">check_circle</div>
          <div id="status-message" class="number">กำลังโอน</div>
        </div>
      `;

      container.appendChild(card);

      if (container.children.length > 5) {
        container.removeChild(container.firstElementChild);
      }

      const statusMessage = card.querySelector("#status-message");
      const loadingIcon = card.querySelector("#status-icon");
      const checkIcon = card.querySelector("#check-icon");

      if (isLatest) {
        setTimeout(() => {
          statusMessage.textContent = "โอนแล้ว";
          loadingIcon.style.display = "none";
          checkIcon.style.display = "inline-block";
        }, 3000);
      } else {
        statusMessage.textContent = "โอนแล้ว";
        loadingIcon.style.display = "none";
        checkIcon.style.display = "inline-block";
      }
    }

    function initializeCards() {
      for (let i = 0; i < 5; i++) {
        const isLatest = i === 4;
        addCard(isLatest);
      }
    }

    setInterval(this.nextSlide, 3000);

    initializeCards();
    setInterval(() => addCard(true), 5000);
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #111;
}

.online-all {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 20px;
  margin: 20px auto;
}

/* สไตล์ของ Online Status */
.user-online-status {
  display: flex;
  align-items: center;
  background-color: #fff;
  border: 1px solid gold; /* ขอบสีเขียว */
  border-radius: 30px; /* ให้มุมโค้ง */
  padding: 10px 30px;
  font-size: 16px;
  color: #ffffff; /* สีเขียว */
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1); /* เงาเบา */
  background-color: rgba(18, 34, 41, 0.3);
}

/* ไอคอนจุดสีเขียว */
.online-icon {
  font-size: 15px;
  color: #28a745; /* สีเขียว */
  margin-right: 10px;
  animation: pulse 1.5s infinite;
}

@keyframes pulse {
  0% {
    transform: scale(1); /* ขนาดเริ่มต้น */
    opacity: 1; /* ปกติ */
  }
  50% {
    transform: scale(0.5); /* ขยายขนาด */
    opacity: 0.7; /* ลดความทึบ */
  }
  100% {
    transform: scale(1); /* กลับสู่ขนาดเดิม */
    opacity: 1; /* กลับความทึบ */
  }
}

.online-num{
  color: gold;
  font-weight: bold;
}

/* คอนเทนเนอร์ของปุ่มทั้งสอง */
.button-container {
  display: flex;
  justify-content: center; /* จัดปุ่มให้อยู่กลาง */
  gap: 15px; /* ระยะห่างระหว่างปุ่ม */
  margin-top: 20px; /* เพิ่มระยะห่างจากข้อความ */
  flex-wrap: wrap; /* ให้ปุ่มเปลี่ยนบรรทัดเมื่อจอเล็ก */
  margin-bottom: 3.25rem;
}

.button-container a {
    text-decoration: none; /* เอาเส้นใต้ */
  }

/* ปุ่มสมัครสมาชิก */
.custom-button1 {
  background-color: gold; /* สีทอง */
  color: black; /* ตัวหนังสือสีดำ */
  padding: 20px 40px; /* ขยายขนาดปุ่ม */
  font-size: 18px; /* ขยายขนาดตัวหนังสือ */
  font-weight: bold;
  border: none;
  border-radius: 30px; /* ทำมุมมน */
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px; /* ระยะห่างระหว่างไอคอนและข้อความ */
  box-shadow: 0px 4px 15px rgba(255, 215, 0, 0.6); /* เงาสีทอง */
  animation: bounce 2s infinite alternate; /* ทำให้ปุ่มกระเด้งๆ*/
}

/* สไตล์เมื่อ hover */
.custom-button1:hover {
  background-color: #ffcc00; /* เปลี่ยนสีเมื่อ hover */
  transform: scale(1.1); /* ขยายขนาดเล็กน้อยเมื่อ hover */
  box-shadow: 0px 8px 25px rgba(255, 215, 0, 0.8); /* เงาที่ใหญ่ขึ้นเมื่อ hover */
}

/* สไตล์เมื่อคลิก */
.custom-button1:active {
  transform: translateY(3px); /* ลดขนาดลงเล็กน้อยเมื่อคลิก */
  box-shadow: 0px 2px 10px rgba(255, 215, 0, 0.4); /* ลดเงาลงเมื่อคลิก */
}

/* การแอนิเมชันกระเด้ง */
@keyframes bounce {
  0% {
    transform: scale(1); /* ขนาดเริ่มต้น */
  }
  50% {
    transform: scale(1.05); /* ขยายขนาดเล็กน้อย */
  }
  100% {
    transform: scale(1); /* กลับสู่ขนาดเดิม */
  }
}

.custom-button1 i {
  font-size: 24px; /* ขนาดไอคอน */
}

/* ปุ่มติดต่อแอดมิน */
.custom-button2 {
  background-color: #00C300; /* สีเขียวแบบไลน์ */
  color: white;
  padding: 20px 40px; /* ขยายขนาดปุ่ม */
  font-size: 18px;
  font-weight: bold;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease; /* เอฟเฟกต์การเปลี่ยนสี */
  box-shadow: 0px 4px 15px rgba(0, 200, 0, 0.6); /* เงาสีเขียว */
}

.custom-button2:hover {
  background-color: #33CC33; /* เปลี่ยนเป็นเขียวอ่อนเมื่อ hover */
  transform: translateY(-3px); /* เพิ่มการเคลื่อนไหวเล็กน้อย */
  box-shadow: 0px 6px 20px rgba(0, 200, 0, 0.8); /* เพิ่มขนาดเงาเมื่อ hover */
}

.custom-button2:active {
  transform: translateY(1px); /* ลดการเคลื่อนไหวเล็กน้อยเมื่อคลิก */
  box-shadow: 0px 2px 10px rgba(0, 200, 0, 0.4); /* ลดขนาดเงาเมื่อ active */
}

/* ปรับขนาดและจัดตำแหน่งปุ่มเมื่อหน้าจอเล็ก */


/* สไตล์สำหรับรูป */
.img-logo {
  max-width: 100%;
  filter: drop-shadow(0 0 10px rgba(255, 215, 0, 1));
}

/* ข้อความที่กระพริบ */
.text1 {
  font-size: 2.2rem;
  font-weight: bold;
  color: white;
  text-align: center;
  display: inline-block;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 1.5rem;
  animation: blink 1s infinite alternate; /* ทำให้กระพริบ */
  animation-delay: 2s;
  text-shadow: 2px 2px 5px rgba(255, 215, 0, 0.8), 0 0 25px gold, 0 0 5px darkgoldenrod;
}

.text2{
  color: white;
}

.text3 {
  font-size: 2.2rem;
  font-weight: bold;
  color: gold;
  text-align: center;
  display: inline-block;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 1.5rem;
  animation: blink 1s infinite alternate; /* ทำให้กระพริบ */
  animation-delay: 2s;
  text-shadow: 2px 2px 5px rgba(255, 215, 0, 0.8), 0 0 25px gold, 0 0 5px darkgoldenrod;
}

.text4 {
  font-size: 2.2rem;
  font-weight: bold;
  color: gold;
  text-align: center;
  display: inline-block;
  padding: 10px;
  border-radius: 5px;
  margin-top: 2.25rem;
  animation: blink 1s infinite alternate; /* ทำให้กระพริบ */
  animation-delay: 2s;
  text-shadow: 2px 2px 5px rgba(255, 215, 0, 0.8), 0 0 25px gold, 0 0 5px darkgoldenrod;
}


/* Animation สำหรับการกระพริบ */
@keyframes blink {
  0% {
    opacity: 1; /* ปกติ */
  }
  50% {
    opacity: 0.7; /* กระพริบลดความทึบ */
  }
  100% {
    opacity: 1; /* ปกติ */
  }
}

     .container2 {
  width: 40%; /* กำหนดความกว้างเป็น 50% */
  margin: 0 auto; /* จัดตำแหน่งให้อยู่ตรงกลาง */
  padding: 10px 30px; 
  background-color: rgba(18, 34, 41, 0.3);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(255, 215, 0, 0.7); /* เงาสีทอง */
  display: flex;
  flex-direction: column-reverse;
  align-items: center; /* จัดแนวกลางแนวตั้ง */
  justify-content: center; /* จัดแนวกลางแนวนอน */
  position: relative; /* เพิ่มตำแหน่งที่สัมพันธ์กับการจัด layout */
  height: auto; /* สูงของคอนเทนเนอร์จะยืดตามเนื้อหา */
}

  @media (max-width: 978px) {
  .container2 {
    width: 95%; /* เปลี่ยนความกว้างเป็น 95% เมื่อความกว้างของหน้าจอน้อยกว่า 978px */
    box-sizing: border-box;
  }
}

    .amount {
  color: gold; /* สีทอง */
  font-weight: bold; /* ตัวหนา */
}

    .card-two {
      width: 100%;
      position: relative;
      flex: 1 0 20%;
      padding: 10px 15px;
      margin: 5px 0;
      background-color: rgba(18, 34, 41, 1);
      border-radius: 8px;
      border: 0.5px solid gold; /* เส้นขอบสีทอง */
      display: flex;
      justify-content: space-between;
      overflow: hidden;
      opacity: 0;
      animation: slideUp 0.5s ease-out forwards;
    }

    /* เอฟเฟกต์คลื่นแสงสีทอง */
    .card-two::before {
      content: "";
      position: absolute;
      top: 0;
      left: -150%;
      width: 150%;
      height: 100%;
      background: linear-gradient(
        120deg,
        transparent 0%,
        rgba(255, 215, 0, 0.2) 50%,
        transparent 100%
      );
      transform: skewX(-20deg);
      animation: shimmer 3s linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    .card-two.speed1::before { animation-duration: 2s; }
    .card-two.speed2::before { animation-duration: 3s; }
    .card-two.speed3::before { animation-duration: 4s; }

    @keyframes shimmer {
      0% { left: -150%; }
      100% { left: 150%; }
    }

    .card-left {
      flex: 0 0 60%;
      display: flex;
      align-items: center;
      justify-content: flex-start;
      z-index: 2;
    }

    .card-right {
      font-size: 15px;
      color: #FFFFFF;
      flex: 0 0 40%;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      gap: 5px;
      z-index: 2;
    }

    .logo-section {
      margin-right: 10px;
    }

    .user-info, .transaction-info {
      font-size: 15px;
      color: white;
      text-align: left;
    }

    .loading-icon {
      width: 20px;
      height: 20px;
      border: 3px solid transparent;
      border-top: 3px solid gold; /* ขอบบนหมุนสีทอง */
      border-radius: 50%;
      animation: spin 1s linear infinite;
    }

    .check-icon {
      font-size: 20px;
      color: gold;
      display: none;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    @keyframes slideUp {
      0% {
        transform: translateY(-100%);
        opacity: 0;
      }
      100% {
        transform: translateY(0);
        opacity: 1;
      }
    }

      /* Container for Cards */
    .card-container {
      display: grid;
      grid-template-columns: repeat(3, 1fr); /* 3 cards in one row */
      gap: 20px;
      padding: 20px;
      width: 90%;
      max-width: 1200px;
      margin: 0 auto; /* Align the container to the center */
    }

    .card {
        position: relative; /* For better control of positioning */
        width: 100%; /* Make the card full-width */
        min-height: 300px;
        overflow: hidden; /* Hide any overflow content */
        border-radius: 15px; /* Optional: rounded corners */
        border: 1px solid gold; /* เส้นขอบสีทอง */
        cursor: pointer;
        opacity: 0.9;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    /* Card Hover Effect */
    .card:hover {
      transform: translateY(-10px);
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
    }

    .badge {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 10px 15px;
  background-color: red; /* พื้นหลังสีแดง */
  color: white;
  font-weight: bold;
  border-radius: 5px;
  font-size: 14px; /* ขนาดฟอนต์ */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2); /* เงาเบา ๆ เพื่อให้ข้อความดูเด่น */
  transition: background-color 0.3s ease; /* เพิ่มการเปลี่ยนสีเมื่อ hover */
  
  /* การกระพริบ */
  animation: blink 1.5s infinite alternate;
}

  .badge:hover {
    background-color: #d9534f; /* สีแดงเข้มเมื่อ hover */
  }

    .online-status {
      width: 100%;
      position: absolute;
      bottom: 0; /* อยู่ที่ด้านล่างสุด */
      left: 50%; /* จัดตำแหน่งแนวนอนให้ตรงกลาง */
      transform: translateX(-50%); /* ปรับตำแหน่งให้ข้อความอยู่ตรงกลาง */
      color: #ffffff; /* เปลี่ยนเป็นสีเขียว */
      font-weight: bold;
      font-size: 1.25rem;
      padding: 10px 0;
      text-shadow: 2px 2px 4px rgba(255, 252, 49, 0.5);
      background-color: transparent; /* ไม่ให้มีพื้นหลัง */
      transition: color 0.3s ease; /* เพิ่มการเปลี่ยนสีเมื่อ hover */
    }

    
.chance-status {
   width: 100%;
  position: absolute;
  bottom: 15%; /* อยู่ที่ด้านล่างสุด */
  left: 50%;
  transform: translateX(-50%); /* จัดให้ตรงกลาง */
  color: rgb(255, 227, 67); /* สีแดง */
  font-weight: bold;
  font-size: 1.35rem;
  text-shadow: 2px 2px 4px rgba(255, 252, 49, 0.5);
  animation: blink 0.7s infinite; /* เรียกใช้งาน animation */
}

    .img-game1 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/game1-2i91UZ_G.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game2 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/game2-BQgt78Ze.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game3 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/game3-DzUyclZQ.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game4 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/game4-ZuWgylAs.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game5 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/game5-5Qse-RS2.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game6 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/game6-CUu9n32g.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    /* Card Title */
    .card-title {
      font-size: 1.5rem;
      font-weight: bold;
      margin-bottom: 10px;
      color: #333;
    }

    .card-description {
      position: absolute; /* Absolute positioning inside card */
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
    }
    /* Responsive Design for smaller screens */
    @media (max-width: 768px) {
      .card-container {
        grid-template-columns: repeat(2, 1fr); /* 2 cards in one row */
      }
      .card {
        min-height: 220px;
    }
     .card-container {
      gap: 15px;
      padding: 1px;
      width: 100%;
    }
    }

    @media (max-width: 480px) {
      .online-status {
      font-size: 1.1rem;
    }
    
      .chance-status {
        font-size: 1.1rem;
      }
    }

    .slider-container {
      position: relative;
      width: 100%;
      max-width: 600px; /* ปรับตามความต้องการ */
      height: 60%;
      margin: auto;
      margin-top: 2.25rem;
      margin-bottom: 2.25rem;
      overflow: hidden;
      border-radius: 15px;
      border: 2px solid #FFD700;
      box-shadow: 0 0 20px rgba(255, 215, 0, 0.6);
    }

    .slider {
      display: flex;
      transition: transform 1s ease;
    }

    .slide {
      min-width: 100%;
      height: 60%;
      position: relative;
    }

    .slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 15px;
    }

    .dots-container {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 10px;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background-color: #FFD700;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .dot.active {
      background-color: #FFCC00;
    }
    
</style>
