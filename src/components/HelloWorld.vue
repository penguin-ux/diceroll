<template>
  <div class="container">
    <h1>確率の壁</h1>
    <div id="diceContainer"></div>
    <p id="rollCount">サイコロを振った回数: 0</p>
    <button id="rollButton">サイコロを振る</button>
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
#app {
  text-align: center;
  margin: 30px auto;
}

.dice {
  display: inline-block;
  width: 50px;
  height: 50px;
  border: 1px solid black;
  text-align: center;
  line-height: 50px;
  margin-right: 10px;
}

.clear {
  font-weight: bold;
  font-size: 20px;
  color: green;
  text-align: center;
}

</style>
