<template>
<div class="contact-us">
  <div class="contact-us__illustration"></div>
  <div class="contact-us__info">
    <div class="contact-us__info__head">Более 569 клиентов уже написали нам</div>
    <div class="contact-us__info__input">
      <input type="text" v-model="inputText">
      <div class="contact-us__info__input__submit">Отправить</div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "ContactUs",
  data: function(){
    return{
      inputText: 'Напишите ваш email'
    }
  }
}
</script>

<style scoped lang="scss">
.contact-us{
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 16.05%;

  .contact-us__info{
    width: 56.05%;

    .contact-us__info__head{
      font-weight: 800;
      font-size: 40px;
      line-height: 54px;
      color: #FFFFFF;
      margin-bottom: 32px;
    }
    .contact-us__info__input{
      display: flex;
      align-items: center;

      input{
        background: #F4F5F7;
        border-radius: 5px 0 0 5px;
        height: 52px;
        width: 248px;
        font-weight: normal;
        font-size: 14px;
        line-height: 24px;
        border: none;
      }
      .contact-us__info__input__submit{
        width: 123px;
        height: 52px;
        font-weight: 500;
        font-size: 14px;
        line-height: 20px;
        color: #FFFFFF;
        background: #18191F;
        border-radius: 0 5px 5px 0;
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }
  }
}
</style>