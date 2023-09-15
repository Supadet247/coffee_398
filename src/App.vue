<script setup>
import { ref } from "vue"

// รายการสถานที่เดินทาง
const travelList = ref([
  { name: "The Good View", time: '10:00-23:00', count: "6/1", price: 200, img: 'https://www.reviewchiangmai.com/wp-content/uploads/2021/12/01_Goodview.png' },
  { name: "Too Nice Nimman", time: '19:00-23:00', count: "6/1", price: 200, img: 'https://www.reviewchiangmai.com/wp-content/uploads/2021/12/02_Too-Nice-Nimman.jpg' },
  { name: "The PARK Society Bar & Hostel", time: '19:00-23:00', count: "6/1", price: 200, img: 'https://www.reviewchiangmai.com/wp-content/uploads/2021/12/03_The-park-society.jpg' },
  { name: "Lism cafe Chiangmai", time: '17:00-00:00', count: "6/1", price: 200, img: 'https://www.reviewchiangmai.com/wp-content/uploads/2021/12/04_Lism-cafe.jpg' },
  { name: "Porjai Bar Chiangmai", time: '18:00-23:50', count: "6/1", price: 200, img: 'https://www.reviewchiangmai.com/wp-content/uploads/2021/12/05_-PORJAI-BAR.jpg' },
  { name: "บางขวาง Cafe’ Chiangmai", time: '17:00-00:00', count: "6/1", price: 200, img: 'https://www.reviewchiangmai.com/wp-content/uploads/2021/12/06_%E0%B8%9A%E0%B8%B2%E0%B8%87%E0%B8%82%E0%B8%A7%E0%B8%B2%E0%B8%87-%E0%B8%84%E0%B8%B2%E0%B9%80%E0%B8%9F%E0%B9%88.jpg' }
]);

// รายการที่จอง
const bookingList = ref([]);

// เพิ่มรายการจอง
function booking(name) {
  bookingList.value.push(name)
}

// จำนวนการจองสำหรับแต่ละสถานที่
const bookingCount = ref(new Array(travelList.value.length).fill(0));

// จองโต๊ะ
function reserveTable(index) {
  bookingCount.value[index] += 1;
}

// ยืนยันการจอง
function confirmBooking() {
  alert("การจองเสร็จสิ้น");
  window.location.reload();
}
</script>

<template>
  <header>Miracle Booking</header>

  <div class="container text-center">
    <div class="row">
      <div class="col mb-4" v-for="(i, index) in travelList" :key="index">
        <div class="card" style="width: 20rem;">
          <img :src="i.img" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">{{ i.name }}</h5>
            <h5>บริการ: {{ i.time }} </h5>
            <h5>จำนวนคนต่อ 1 โต๊ะ: {{ i.count }}</h5>
            <h5>ค่าบริการ:{{ i.price }}</h5>
            <button @click="reserveTable(index)" class="main-button">จองโต๊ะ</button>
            <p>จำนวนการจอง: <span>{{ bookingCount[index] }}</span></p>
          </div>
        </div>
      </div>
    </div>
  </div>

  <footer>
    <div class="form-user-buy">
      <div id="fullname+phonenum+date+time">
        ชื่อที่จอง: <input type="text" name="name" id="flname">
        เบอร์โทรศัพท์: <input type="tel" name="p_num" id="phone_number">
        วันที่: <input type="text" name="date_local" id="date_local" placeholder="ระบุว (dd/mm/yyyy)">
        เวลา: <input type="time" name="time_local" id="time_local">
      </div>
    </div>
    <div class="footer-content">
      <a href="#" class="bottom-button" @click="confirmBooking">ยืนยัน</a>
    </div>
  </footer>
</template>
