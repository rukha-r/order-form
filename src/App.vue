<template>
<div class="outer-body">

<div class="main-wrapper">
<img id="current-image" :src="product.images[0]">
<div class="images">
      <div v-for="image of product.images" :key='image'>
        <img :src='image' @click='updateCurrentImage(image)'>
      </div>
    </div>
    <h3 class="header">VARSK 4'ü 1 Arada Araç Süpürgesi</h3>
   <h4>{{ product.price }}</h4>
   <div class="kargo">
   <p>UCRETSIZ KARGO</p>
   </div>
    <div class="description">
      <p>İpuçları: Zayıf Emiş Gücü Sorunlarıyla Karşılaşıyorsanız, Lütfen Hepa Filtresini Zamanında Temizleyin</p>
      <p>4'ü 1 arada ： VARSK, tek bir taşınabilir makinede hem vakumlu temizleme hem de lastik şişirme özelliğine sahiptir ("I" modu vakumlamak içindir, "II" modu şişirmek içindir). Bu iki temel işlevin yanı sıra, dijital lastik basıncı LCD ekranı kolayca okuyabilir ve yerleşik LED çalışma ışığı, karanlıkta çalıştırıldığında ekstra güvenlik ve güvenlik sağlamak için çevrenizi aydınlatır.</p>
      <div class="video">
        <video :src="product.video" :poster="product.poster" controls></video>
      </div>
      <p>Artık Lastik Yok! VARSK hava kompresörü lastik şişirici ile, hiçbir yerde patlak lastik konusunda asla endişelenmeyeceksiniz. 35L / MIN (1.24 CFM) Hızlı Şişirme Hızı: Yüksek verimli doğrudan tahrikli motor, 195 / 65R15 otomobil lastiğini 6 dakikada 0'dan 35 psi'ye şişirebilir. Önceden ayarlanmış basınca ulaşıldığında otomatik olarak durur. Yolda cankurtaran olacak. 150 PSI'ye kadar maksimum basınçla, çoğu şişme, top, motosiklet, sedan ve SUV ile başa çıkabilir, ancak yüksek basınçlı karavan ve kamyon lastikleri için geçerli değildir.</p>
    </div>
    <div class="form-holder">
    <form>
      <h4>HIZLI SIPARIS FORMU</h4>
        <h5>Adet</h5>
          <select id="quantity">
            <option value="1">1 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="2">2 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="3">3 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="4">4 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="5">5 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="6">6 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="7">7 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="8">8 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="9">9 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
            <option value="10">10 VARSK 4'ü 1 Arada Araç Süpürgesi</option>
          </select>
        <h5>Odeme Tipi Seciniz</h5>
        <select id="payment_type">
          <option value="kapida nakit odeme">Kapida Nakit Odeme</option>
          <option value="kapida kart ile odeme">Kpida Kredi Karti ile Odeme</option>
        </select>
        <h5>Detay</h5>
        <input id="name" type="text" placeholder="Adiniz" required>
        <input id="surname" type="text" placeholder="Soyadiniz" required>
        <input id="phone" type="tel" placeholder="Telefon numaraniz" required>
        <input id="province" type="text" placeholder="Il seciniz" required>
        <input id="city" type="text" placeholder="Ilce seciniz" required>
        <textarea id="full_address" type="text" placeholder="Acik adresinizi giriniz (Sokak,ev,bina,ev numarasi)..." required></textarea>
        <input type="submit" value="Siparisi Gonder" @click="sendOrder()">
    </form>
   </div>
   <div class="security">
   <div v-for="infoImg of product.security" :key="infoImg">
     <img :src="infoImg">
   </div>
   </div>
   <hr>
   <footer>
     Copyright &copy; {{year}} VARSK
   </footer>
   </div>

   <div class="order">
     <div class="by_phone">
       <a :href="admin_number">&phone; TELEFONLA SIPARIS</a>
     </div>
     <div class="by_whatsapp">
       <a :href="admin_whatsapp">&#x2709; WHATSAPP SIPARIS</a>
     </div>
   </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      admin: '905528128965',
      product: {
        price: '245.99 TL',
        images: [
          require('./images/pr1.jpg'),
          require('./images/pr2.jpg'),
          require('./images/pr3.jpg'),
          require('./images/pr4.jpg'),
          require('./images/pr5.jpg'),
          require('./images/pr6.jpg')
        ],
        poster: require('./images/poster.png'),
        video: require('./images/advert.mp4'),
        security: [
          require('./images/info2.png'),
          require('./images/info3.png')
        ]
      }
    }
  },
  methods: {
    updateCurrentImage(el){
      document.querySelector('#current-image').src = el;
    },
    sendOrder(){
      let quantity = document.querySelector('#quantity').value;
      let payment_type = document.querySelector('#payment_type').value;
      let name = document.querySelector('#name').value;
      let surname = document.querySelector('#surname').value;
      let phone_number = document.querySelector('#phone').value;
      let province = document.querySelector('#province').value;
      let city = document.querySelector('#city').value;
      let full_address = document.querySelector('#full_address').value;
      let order_details = `
      Adi: ${name}
      Soyadi: ${surname}
      Telefon numarasi: ${phone_number}
      Il: ${province}
      Ilce: ${city}
      Ev adresi: ${province}, ${city}, ${full_address}
      Adet:${quantity}
      Odama turu: ${payment_type}
      `
      if(quantity && payment_type && name && surname && phone_number && province && city && full_address){
         window.open(`https://wa.me/${this.admin}?text=${order_details}`, '_blank')
         }
         else {
            alert('Please,fill the form and try again!');
          }
    }
  },
  computed: {
    year(){
      let d = new Date();
      return d.getFullYear();
    },
    admin_number(){
      return `tel:+${this.admin}`
    },
    admin_whatsapp(){
      return `https://api.whatsapp.com/send?phone=${this.admin}, '_blank'`;
    }
  }
}
</script>

<style lang="scss">
body {
  text-align: center;
}
* {
  margin: 0;
  padding: 0;
  font-family: arial;
}
.main-wrapper {
  width: 100%;
  height: 100%;
  position: absolute;
  z-index: 0;
  overflow: scroll;
  #current-image {
    min-width: 100%;
  }
  p {
    padding: 15px;
  }
  .kargo {
    padding: 10px;
    display: flex;
    justify-content: center;
    animation: blink 1s ease-in-out infinite alternate;
    p {
    background-color: green;
    color: white;
    padding: 7px;
    width: 150px;
    align-items: center;
    border-radius: 20px;
    box-shadow: 0 0 15px gray;
    }
    @keyframes blink {
      from {opacity: 1}
      to {opacity: 0}
    }
  }
  .images {
    display: grid;
    grid-template-columns: repeat(6,auto);
    img {
      width: 100%;
      opacity: .6;
      &:hover {
        opacity: 1;
     }
    }
  }
  .video {
    video {
    width: 100%;
    height: 100%;
   }
  }
  .form-holder {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    form {
      max-width: 75%;
      box-shadow: 0 0 20px gray;
      border-radius: 5px;
      margin: 30px;
      padding: 20px 0 20px 0;
      background-color: #bdbdbd63;
    input,
    select,
    textarea {
      width: 70%;
      padding: 10px;
      margin: 10px;
      font-size: 13px;
      border-radius: 5px;
      border: none;
      text-align: center;
      &:last-child {
        text-align: center;
        background-color: green;
        color: white;
        font-size: 13px;
      }
    }
    select {
      padding: 5px;
    }
   }
  }
  .security {
   display: grid;
   grid-template-columns: repeat(2,auto);
   img {
     width: 70%;
   }
  }
  hr {
   color: rgba(97, 97, 97, 0.26);
  }
  footer {
   margin: 15px;
   color: rgba(102, 100, 100, 0.774);
  }
}
.order {
  position: absolute;
  z-index: 1;
  text-align: center;
  bottom: 0;
  font-size: 12px;
  cursor: pointer;
  .by_phone {
    width: 160px;
    background-color: black;
    margin: 5px 0;
    padding: 10px 0 10px 0;
    border-radius: 0 5px 5px 0;
    a {
      text-decoration: none;
      color: white;
    }
  }
  .by_whatsapp{
    @extend .by_phone;
    background-color: green;
  }
}
</style>
