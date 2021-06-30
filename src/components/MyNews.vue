<template>
<div class="news-block">
  <h2 class="news-block__head">Новости</h2>
  <div class="news-block__big-news">
    <div class="news-block__big-news__image" :id="'id' + idMain"></div>
    <div class="news-block__big-news__info">
      <div class="news-block__big-news__info__preview">
        <div class="news-block__big-news__info__preview__category">{{codeMain}}</div>
        <svg width="15" height="1" viewBox="0 0 15 1" fill="none" xmlns="http://www.w3.org/2000/svg">
          <line y1="0.5" x2="15" y2="0.5" stroke="#DEDEDE"/>
        </svg>
        <div class="news-block__big-news__info__preview__time">{{idMain}}</div>
      </div>
      <h3 class="news-block__big-news__info__head">
        {{itemMain}}
      </h3>
      <article class="news-block__big-news__info__article" v-html="previewHTML"></article>
      <a href="#" class="news-block__big-news__info__more">Читать дальше<svg width="16" height="10" viewBox="0 0 16 10" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M10.1953 1.47132C9.93491 1.21097 9.93491 0.788864 10.1953 0.528514C10.4556 0.268165 10.8777 0.268165 11.1381 0.528514L15.1381 4.52851C15.3984 4.78886 15.3984 5.21097 15.1381 5.47132L11.1381 9.47132C10.8777 9.73167 10.4556 9.73167 10.1953 9.47132C9.93491 9.21097 9.93491 8.78886 10.1953 8.52851L13.0572 5.66657H1.34052C0.968273 5.66657 0.666504 5.3681 0.666504 4.99991C0.666504 4.63172 0.968273 4.33324 1.34052 4.33324H13.0572L10.1953 1.47132Z" fill="#8C30F5"/>
      </svg>
      </a>
    </div>
  </div>
  <div class="news-block__list-of-news" :style="{marginLeft: toLeft + 'px'}">
    <div class="news-block__list-of-news__overlay">
      <svg @click="goLeft" width="52" height="51" viewBox="0 0 52 51" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M35.2627 17.6062C34.6939 17.0375 33.8002 17.0375 33.2314 17.6062C32.6627 18.175 32.6627 19.0688 33.2314 19.6375L37.1314 23.6187H13.1627C12.3502 23.6187 11.7002 24.2687 11.7002 25.0812C11.7002 25.8937 12.3502 26.5438 13.1627 26.5438H37.1314L33.2314 30.525C32.6627 31.0937 32.6627 31.9875 33.2314 32.5562C33.4752 32.8 33.8814 32.9625 34.2064 32.9625C34.6127 32.9625 34.9377 32.8 35.1814 32.5562L39.6502 28.0063C41.1939 26.4625 41.1939 23.9437 39.6502 22.4L35.2627 17.6062Z" fill="#747579"/>
        <path d="M26.0001 0.0561523C12.1876 0.0561523 0.975098 11.1874 0.975098 24.9999C0.975098 38.8124 12.1876 50.0249 26.0001 50.0249C39.8126 50.0249 51.0251 38.8124 51.0251 24.9999C51.0251 11.1874 39.8126 0.0561523 26.0001 0.0561523ZM26.0001 47.1812C13.8126 47.1812 3.81885 37.1874 3.81885 24.9999C3.81885 12.8124 13.8126 2.8999 26.0001 2.8999C38.1876 2.8999 48.1813 12.8124 48.1813 24.9999C48.1813 37.1874 38.1876 47.1812 26.0001 47.1812Z" fill="#747579"/>
      </svg>
    </div>
    <div class="news-block__list-of-news__info" v-for="(item, idx) in items" :key="idx">
      <div class="news-block__list-of-news__info__image" :id="'id' + id[idx]"></div>
      <div class="news-block__list-of-news__info__preview">
        <div class="news-block__list-of-news__info__preview__category">{{code[idx]}}</div>
        <svg width="15" height="1" viewBox="0 0 15 1" fill="none" xmlns="http://www.w3.org/2000/svg">
          <line y1="0.5" x2="15" y2="0.5" stroke="#DEDEDE"/>
        </svg>
        <div class="news-block__list-of-news__info__preview__time">{{id[idx]}}</div>
      </div>
      <h3 class="news-block__list-of-news__info__head">
        {{item}}
      </h3>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "MyNews",
  data: function(){
    return{
      items: [], code: [], id: [],
      itemMain: '', codeMain: '', idMain: '', previewMain: '',
      toLeft: 0
    }
  },
  computed:{
    previewHTML: function (){
      return this.previewMain.split('').splice(0, 290).join('');
    }
  },
  methods:{
    goLeft: function (){
      if (this.toLeft > -960){
        this.toLeft -= 320;
      }else{
        alert('Have a good day! :-)');
        this.toLeft = 0;
      }
    }
  },
  created: async function() {
    let url = 'https://b24crm-nst.s11.itua.in.ua/rest/513/tz8j9hozz843f81k/lists.element.get.json?IBLOCK_TYPE_ID=lists&IBLOCK_ID=153&ELEMENT_ORDER%5bID%5d=DESC';
    let response = await fetch(url);
    let comits = await response.json();
    console.log(comits);
    comits.result.forEach((comit,index) => {
      if (index) {
        this.items.push(comit['NAME']);
        this.code.push(comit['CODE']);
        this.id.push(comit['ID']);
      } else{
        this.itemMain = comit['NAME'];
        this.codeMain = comit['CODE'];
        this.previewMain = comit['PREVIEW_TEXT'];
        this.idMain = comit['ID'];
      }
    });
  }
}
</script>

<style scoped lang="scss">
$primary-black: #18191F;
$primary-violet: #8C30F5;
$primary-orange: #FE9A22;
$primary-grey: #DEDEDE;

%flex-block{
  display: flex;
  align-items: center;
}

.news-block{
  margin-top: 150px;

  .news-block__head{
    color: $primary-black;
    font-weight: 800;
    font-size: 48px;
    line-height: 64px;
  }

  .news-block__big-news{
    @extend %flex-block;

    .news-block__big-news__info{
      margin-left: 30px;

      .news-block__big-news__info__preview{
        @extend %flex-block;
        .news-block__big-news__info__preview__category{
          color: $primary-violet;
          font-weight: 500;
          font-size: 14px;
          line-height: 12px;
          letter-spacing: 1px;
          margin-right: 10px;
        }
        .news-block__big-news__info__preview__time{
          color: $primary-grey;
          font-weight: normal;
          font-size: 14px;
          line-height: 12px;
          margin-left: 10px;
        }
      }

      .news-block__big-news__info__head{
        color: $primary-black;
        font-weight: 600;
        font-size: 24px;
        line-height: 130%;
        margin-bottom: 16px;
      }
      .news-block__big-news__info__article{
        color: $primary-black;
        font-weight: normal;
        font-size: 16px;
        line-height: 160%;
      }
      .news-block__big-news__info__more{
        color: $primary-violet;
        display: block;
        font-weight: 500;
        font-size: 14px;
        line-height: 16px;
        margin-top: 24px;
        svg{
          margin-left: 9px;
        }
      }
    }
  }

  .news-block__list-of-news{
    @extend %flex-block;
    padding-top: 60px;
    position: relative;
    transition: 1s;

    .news-block__list-of-news__overlay{
      position: absolute;
      width: 100vw;
      height: 100%;
      left: 94%;
      top: 0;
      background: #FFFFFF;
      opacity: 0.6;

      svg{
        left: 1%;
        position: absolute;
        top: calc(50% - 25px);
      }
    }

    .news-block__list-of-news__info{
      margin-right: 30px;

      .news-block__list-of-news__info__image{
        width: 320px;
        height: 320px;
        background-repeat: no-repeat;
        background-size: cover;
        border-radius: 8px;
      }
      .news-block__list-of-news__info__preview{
        @extend %flex-block;
        padding-top: 24px;
        padding-bottom: 16px;

        .news-block__list-of-news__info__preview__category{
          color: $primary-violet;
          font-weight: 500;
          font-size: 14px;
          line-height: 12px;
          letter-spacing: 1px;
          margin-right: 10px;
        }
        .news-block__list-of-news__info__preview__time{
          color: $primary-grey;
          font-weight: normal;
          font-size: 14px;
          line-height: 12px;
          margin-left: 10px;
        }
      }
      .news-block__list-of-news__info__head{
        color: $primary-black;
        font-weight: 600;
        font-size: 24px;
        line-height: 130%;
      }
    }
  }
}
@media (max-width: 580px) {
  .news-block__big-news{
    flex-direction: column;
  }
  #id47936{
    width: 100%!important;
    border-radius: 5px!important;
  }
  .news-block__big-news__info{
    margin-left: 0!important;
    margin-top: 24px!important;
  }
  .news-block__big-news__info__head{
    margin-top: 16px!important;
  }
}
</style>