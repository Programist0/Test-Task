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
  <div class="news-block__list-of-news" v-for="(item, idx) in items" :key="idx">
    <div class="news-block__list-of-news__image" :id="'id' + id[idx]"></div>
    <div class="news-block__list-of-news__info">
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
      itemMain: '', codeMain: '', idMain: '', previewMain: ''
    }
  },
  computed:{
    previewHTML: function (){
      return this.previewMain.split('').splice(0, 290).join('');
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
}
</style>