
<template>
  <div class="top-bar">
    <div class="inner">
      <div class="inner__info">
        <h1>Делаем больше чем просто SEO</h1>
        <article class=" inner__info__article ">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc odio in et, lectus sit lorem id integer.
        </article>
        <div class="contact-us">
          Связаться с нами
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopBar"
}
</script>

<style scoped lang="scss">
$font-def: 'Inter', sans-serif;
$primary-black: #18191F;
$primary-violet: #8C30F5;
$primary-orange: #FE9A22;
$primary-grey: #F4F5F7;

.top-bar{
  font-family: $font-def;
  width: 100%;
  height: 708px;
  background-size: cover;
  background-position-y: -72px;
  background-repeat: no-repeat;

    .inner__info {
      width: 55.12%;
      padding-top: 176px;

      h1 {
        font-weight: 800;
        font-size: 72px;
        line-height: 98px;
        margin-bottom: 16px;
      }

      .inner__info__article {
        font-weight: normal;
        font-size: 18px;
        line-height: 32px;
        margin-bottom: 32px;
      }

      .contact-us {
        color: #fff;
        font-weight: 500;
        font-size: 16px;
        line-height: 24px;
        width: 205px;
        height: 48px;
        padding: 12px 32px;
        background: #8C30F5;
        border-radius: 6px;
        text-align: center;
      }
    }

}
</style>