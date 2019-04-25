<template>
  <div id="translateOutput">
    <h2>{{translatedText}}</h2>  
  </div>
</template>

<script>
  export default {
    name: 'translateOutput',
    props:[
      'translatedText'
    ],
  }
</script>

<style lang="scss">
  #translateOutput{
    color: green;
    font-size: 2rem;
  }
</style>
