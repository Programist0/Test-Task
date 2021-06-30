<template>
  <div class="info">
    <h2>Наши услуги</h2>
    <div class="info__content">
      <div class="info__content__item" v-for="(item, idx) in items" :key="idx" :id="'id' + id[idx]">
        <h3 class="info__content__item__head">{{item}}</h3>
        <article class="info__content__item__article" v-html="infos[idx]"></article>
        <a :href="code[idx]" class="info__content__item__href">Подробнее</a>
      </div>
    </div>
    <div class="info__href">
      <a href="#">Связаться с нами</a>
      <svg width="22" height="14" viewBox="0 0 22 14" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M14.2931 1.70711C13.9026 1.31658 13.9026 0.683417 14.2931 0.292893C14.6837 -0.0976311 15.3168 -0.0976311 15.7074 0.292893L21.7073 6.29289C22.0979 6.68342 22.0979 7.31658 21.7073 7.70711L15.7074 13.7071C15.3168 14.0976 14.6837 14.0976 14.2931 13.7071C13.9026 13.3166 13.9026 12.6834 14.2931 12.2929L18.586 7.99998H1.01103C0.452653 7.99998 0 7.55227 0 6.99998C0 6.4477 0.452653 5.99998 1.01103 5.99998H18.586L14.2931 1.70711Z" fill="#18191F"/>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyServises",
  data: function(){
    return{
      items: [], infos: [], code: [], id: []
    }
  },
  created: async function() {
    let url = 'https://b24crm-nst.s11.itua.in.ua/rest/513/tz8j9hozz843f81k/lists.element.get.json?IBLOCK_TYPE_ID=lists&IBLOCK_ID=152&ELEMENT_ORDER%5bID%5d=ASC';
    let response = await fetch(url);
    let comits = await response.json();
    comits.result.forEach(comit => {
      this.infos.push(comit['PREVIEW_TEXT']);
      this.items.push(comit['NAME']);
      this.code.push(comit['CODE']);
      this.id.push(comit['ID']);
    });
  }
}
</script>

<style scoped lang="scss">
$font-def: 'Inter', sans-serif;
$primary-black: #18191F;
$primary-violet: #8C30F5;
$primary-orange: #FE9A22;
$primary-grey: #F4F5F7;

.info{
  font-family: $font-def;
  padding: 150px 0;

  h2{
    font-weight: 800;
    font-size: 48px;
    line-height: 64px;
    text-align: center;
    font-feature-settings: 'salt' on, 'liga' off;
    color: $primary-black;
  }

  .info__href{
    display: flex;
    align-items: center;
    padding: 12px 20px;
    border: 1px solid #18191F;
    border-radius: 6px;
    width: 221px;
    margin: 0 auto;
    transition: 0.5s;
    
    &:hover{
      background-color: #fff;
    }
    a{
      padding-right: 17px;
    }
  }

  .info__content{
    margin-top: 48px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;

    .info__content__item{
      height: 346px;
      margin-bottom: 76px;
      width: 32%;
      border-radius: 8px;
      background-size: cover;
      padding-bottom: 40px;
      top: 40px;
      justify-content: flex-end;
      display: flex;
      flex-direction: column;


      &:hover{
        background-image: none!important;
        background-color: #fff!important;
      }
      .info__content__item__head{
        font-weight: 600;
        font-size: 24px;
        line-height: 32px;
        margin-left: 9.14%;
        padding-bottom: 12px;
        color: $primary-black;
      }
      .info__content__item__article{
        font-weight: normal;
        font-size: 16px;
        line-height: 26px;
        color: $primary-black;
        width: 81.71%;
      }
      .info__content__item__href{
        font-weight: 500;
        font-size: 14px;
        line-height: 16px;
        padding-top: 40px;
        color: $primary-violet;
      }
      .info__content__item__article, .info__content__item__href{
        display: none;
        
      }

    }
  }
}
.info__content__item:hover .info__content__item__article, .info__content__item:hover .info__content__item__href{
  display: block!important;
  margin-left: 9.14%;
}
@media (max-width: 580px) {
  .info{
    overflow: hidden!important;
  }
  .info__content {
    width: 200vw !important;
  }
}
</style>