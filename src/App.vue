
<script>
import 'boxicons'
import { computed } from 'vue'
export default {
  data(){
    return {
      question: "",
      answer: "Questions usually contain a question mark. ;-",
      loading: false,
      price: 10000

    }
  },
  watch: {
    question(newQuestion, oldQuestion){
      if(newQuestion.includes('?')){
        this.getAnswer()
      }
    }
  },
  methods: {
    async getAnswer() {
      this.loading = true
      this.answer = 'Thinking...'
      try {
        const res = await fetch('http://yesna.wtf/api')
        this.answer = (await res.json()).answer
      } catch(error){
        this.answer = 'Error! Could not reach the API.' + error
      }finally {
        this.loading = false
      }
    }
  },
  computed: {
      nowData(){
        return new Date().getHours();
      },
      discount() {
        return this.price * 0.85;
      },
  }
}
</script>

<template>
  <div class="asosiy">
    <img src="./assets/img/orqaga.svg" alt="">
    <h1>Tanlashni davom etiring</h1>
    <h3>Bizning Telefonlarimiz:</h3>
    <h3>+996 705 188 955</h3>
    <h3>+ 996555 188 955</h3>
    <p><img src="./assets/img/time.svg" alt="">10:00 dan 00:00 gacha ishlaymiz</p>
  </div><br>
  <div>
    <h1>MA'LUMOTLARINGIZ</h1>
    <div>
      <form action="">
      <input type="number" name="" id="" placeholder="telefon">
      <input type="text" placeholder="Name"><br>
      <button><img src="./assets/img/wallet.svg" alt="">naxt pul</button>
      <button><img src="./assets/img/card.svg" alt="">karta</button><br>
      <input type="checkbox">
      <span>Подготовить сдачу с</span>
      <input type="number" placeholder="Сумма">
      <p>палочки + соусник обычный <img src="./assets/img/minus.svg" alt=""> 10 <img src="./assets/img/plus.svg" alt=""></p>
      <p>палочки + соусник обычный <img src="./assets/img/minus.svg" alt=""> 10 <img src="./assets/img/plus.svg" alt=""></p>
      <input type="text" placeholder="Введите промокод">
      </form>
    </div>
  </div>
    <div>
      <form action="">
        <button>Курьером</button>
        <button>Самовывоз</button><br>
        <input type="text" placeholder="Улица">
        <input type="text" placeholder="Дом"><br>
        <input type="text" placeholder="Кв">
        <input type="text" placeholder="Подъезд">
        <input type="text" placeholder="Етаж">
        <input type="text" placeholder="Код"><br>
        <button>На сейчас</button>
        <button>На время</button><br>
        <input type="text" placeholder="E-mail(необязательно)">
      </form>
    </div>
  <button>Оформить заказ</button>
</template>

<style lang="scss">
</style>>


