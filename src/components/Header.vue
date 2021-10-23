<template>
  <el-header>
    <el-col>进销存管理系统</el-col>
    <el-col>
      <el-avatar shape="square" :size="50" :src="squareUrl"></el-avatar>
    </el-col>
  </el-header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      circleUrl: "https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png",
      squareUrl: "https://cube.elemecdn.com/9/c2/f0ee8a3c7c9638a54940382568c9dpng.png",
      sizeList: ["large", "medium", "small"]
    }
  }
}
</script>

<style scoped>

</style>