<template>
    <section>
      <!-- 是否登录 -->
      <login-welcome></login-welcome>
      <!-- 今日赠言 -->
      <tip-card></tip-card>
      <!-- 资源推介 -->
      <PromotionCard></PromotionCard>
    </section>
  </template>
  
  <script>

  import TipCard from '@/views/card/Tip'
  import PromotionCard from '@/views/card/Promotion'
  import LoginWelcome from '@/views/card/LoginWelcome'
  
  export default {
    name: "CardBar",
    components: { LoginWelcome, PromotionCard, TipCard }
  }
  
  </script>
