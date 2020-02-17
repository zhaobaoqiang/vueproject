<template>
  <div class="hello">
    <div class="div1">111</div>
    <div class="div2">222</div>
    <div class="div3">333</div>
    <div class="div4">444</div>
    <div class="div5">555</div>
    <p class="serif">这一段的字体是 Times New Roman </p>
    <p class="sansserif">这一段的字体是 Arial.</p>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello
{
  position: absolute;
  left: 50px;
  width:calc(100% - 100px);
  background-color:violet;
  display: flex;
  flex-direction: column;
}
.div1{
  background-color: blue;
}
.div5{
  background-color: blueviolet;
}
.serif
{
  font-family: 'Times New Roman', Times, serif;
}
.sansserif
{
  font-family: Arial, Helvetica, sans-serif;
  font-size: 10;
}
</style>
