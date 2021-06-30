<template>
  <MyHeader></MyHeader>
  <TopBar></TopBar>
  <div class="servises">
    <div class="inner">
      <MyServises></MyServises>
    </div>
  </div>
  <div class="news">
    <div class="inner">
      <ContactUs></ContactUs>
      <MyNews></MyNews>
    </div>
  </div>
  <MyFooter></MyFooter>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import TopBar from './components/TopBar.vue'
import MyServises from './components/MyServises.vue'
import ContactUs from './components/ContactUs.vue'
import MyNews from './components/MyNews.vue'
import MyFooter from './components/MyFooter.vue'

export default {
  name: 'App',
  components: {
    MyHeader, TopBar, MyServises, ContactUs, MyNews, MyFooter
  }
}
</script>

<style lang="scss">

$font-def: 'Inter', sans-serif;
$primary-black: #18191F;
$primary-violet: #8C30F5;
$primary-orange: #FE9A22;
$primary-grey: #F4F5F7;

*{
  font-family: $font-def;
  font-style: normal;
}

.inner{
  width: 77.08%;
  margin: 0 auto;
  height: 100%;
}

.servises{
  height: 1276px;
  background: #F4F5F7;
  width: 100%;
}

.news{
  width: 100%;
  height: 1750px;
}
</style>
