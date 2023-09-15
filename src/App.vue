<template>
  <div class="coffee-shop-app">
    <h1>ร้านกาแฟ<br> 
    กรุณาเลือกร้านที่ต้องการจอง</h1>
    <div class="coffee-shops">
      <div v-for="(shop, index) in coffeeShops" :key="index" class="coffee-shop">
        <h2>{{ shop.name }}</h2>
        <p>{{ shop.description }}</p>
        <button @click="reserveTable(shop)">จองโต๊ะ</button>
        
      </div>
    </div>
    
    <div v-if="reservation" class="reservation-details">
      <h2>ข้อมูลการจอง</h2>
      <p><strong>ชื่อ:</strong> {{ reservation.name }}</p>
      <p><strong>เบอร์โทร:</strong> {{ reservation.phone }}</p>
      <p><strong>วันที่:</strong> {{ reservation.date }}</p>
      <p><strong>เวลา:</strong> {{ reservation.time }}</p>
      <p><strong>จำนวนโต๊ะ:</strong> {{ reservation.tableCount }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      coffeeShops: [
        {
          name: 'ร้านกาแฟสไตล์โบราณสวนกาแฟ@แม่โจ้',
          description: 'บ้านพัฒนาทรายแก้ว 17นั่งรับประทานที่ร้านสั่งกลับบ้าน'
          
          
        },
        {
          name: 'The Nest Cafe',
          description: 'บรรยากาศดีใกล้ชิดธรรมชาติ จัดเต็มทั้งอาหารเหนือ อาหารพื้นเมือง และเครื่องดื่มหลากหลาย'
        },
        {
          name: 'Looper & Co',
          description: 'ร้านกาแฟในเชียงใหม่กับบาริสต้ามากฝีมือ ดีกรีแชมป์ และเมนูที่แสดงความครีเอทีฟ ทั้งกาแฟและเครื่องดื่ม ไม่ควรพลาดทั้งกาแฟแบบคลาสสิกที่หอมกาแฟชัดเจน'
        }
      ],
      reservation: null
    };
  },
  methods: {
    reserveTable(shop) {
      const name = prompt('กรุณากรอกชื่อ:');
      const phone = prompt('กรุณากรอกเบอร์โทร:');
      const date = prompt('กรุณาระบุวันที่:');
      const time = prompt('กรุณาระบุเวลา:');
      const tableCount = parseInt(prompt('กรุณาระบุจำนวนโต๊ะ:'));

      if (name && phone && date && time && tableCount > 0) {
        this.reservation = {
          name,
          phone,
          date,
          time,
          tableCount
        };
      } else {
        alert('กรุณากรอกข้อมูลให้ครบถ้วน');
      }
    }
  }
};
</script>

<style scoped>
.coffee-shop-app {
  flex: auto;
  background-image: url(/src/assets/c4.jpg);
  text-align: center;
  font-family: Arial, sans-serif;
  background-color: #dfdfdf; /* Updated background color */
  padding: 140px;
}

h1 {
  color: #000000; /* White text color */
}

h3 {
  color: #353434; /* Light gray text color for instructions */
}

.coffee-shops {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

.coffee-shop {
  flex: auto;
  border: 1px solid #ccc;
  background-color: #fff;
  padding: 80px;
  margin: 80px;
  border-radius: 8px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  opacity: 0.9;
  filter: alpha(opacity=60); /* For IE8 and earlier */
}

button {
  background-color: #007BFF;
  color: #fff;
  border: none;
  padding: 8px 16px;
  cursor: pointer;
  border-radius: 4px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #db8c8c;
}

.reservation-details {
  flex: auto;
  margin-top: 20px;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}
h1,h3 {margin: 30px;
  background-color: #ffffff;
  border: 1px solid black;
  opacity: 0.8;
  filter: alpha(opacity=60); /* For IE8 and earlier */
}

div.transbox p {
  margin: 5%;
  font-weight: bold;
  color: #000000;
}

</style>


