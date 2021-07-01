<template>
<div class="contact-us">
  <div class="contact-us__illustration"></div>
  <div class="contact-us__info">
    <div class="contact-us__info__head">Более 569 клиентов уже написали нам</div>
    <div class="contact-us__info__push">{{inputInfo}}</div>
    <div class="contact-us__info__input">
      <input type="text" :placeholder="inputPlaceholder" v-model="inputText" id="contact-us__info__input__text">
      <div class="contact-us__info__input__submit" @click="inputSend">Отправить</div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "ContactUs",
  data: function(){
    return{
      inputText: '', inputPlaceholder: 'Напишите ваш email', inputInfo: ''
    }
  },
  methods:{
    inputSend: function (){
      this.inputText = '';
      this.inputInfo = 'Отправлено успешно!';
      setTimeout(() => this.inputInfo = '', 2000);
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

    .contact-us__info__push{
      color: #FFFFFF;
      font-size: 14px;
      line-height: 24px;
      height: 20px;
    }
    .contact-us__info__head{
      font-weight: 800;
      font-size: 40px;
      line-height: 54px;
      color: #FFFFFF;
      margin-bottom: 12px;
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
        cursor: pointer;
        transition: 1s;
        &:hover{
          background: #555;
        }
      }
    }
  }
}
@media (max-width: 580px) {
  .contact-us {
    height: 715px!important;
    flex-direction: column!important;
    padding: 0!important;
    justify-content: center!important;
  }
  .contact-us__info__input{
    flex-direction: column!important;
  }
  .contact-us .contact-us__info{
    text-align: center!important;
    width: 85%!important;
  }
  .contact-us__info__input input{
    border-radius: 5px!important;
  }
  .contact-us__info__input__submit{
    border-radius: 5px!important;
    margin-top: 16px;
  }
}

</style>