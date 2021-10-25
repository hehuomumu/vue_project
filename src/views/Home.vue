<template>
  <el-container class="home">
    <el-header class="header">
      <el-row type="flex" justify="space-between" align="middle">
        <div class="title">
          <router-link to="/home">
            <img src="../assets/logo.png" alt="logo">
            进销存管理系统
          </router-link>
        </div>
        <div>
          <el-dropdown class="dropdown">
          <span class="el-dropdown-link">
            <el-avatar :size="30" :src="squareUrl"></el-avatar>
            {{ userInfo.name }}
          </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item icon="el-icon-user">个人中心</el-dropdown-item>
              <el-dropdown-item icon="el-icon-switch-button">退出登录
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </div>
      </el-row>
    </el-header>
    <el-container>
      <el-aside class="body" :width="width">
        <el-menu class="el-menu-vertical-demo" :collapse="isCollapse"
                 background-color="#545c64" text-color="#fff"
                 active-text-color="#ffd04b">
          <el-menu-item index="1">
            <i class="el-icon-goods"></i>
            <span slot="title">商品基础设置</span>
          </el-menu-item>
          <el-menu-item index="2">
            <i class="el-icon-s-shop"></i>
            <span slot="title">门店基础设置</span>
          </el-menu-item>
          <el-menu-item index="3">
            <i class="el-icon-suitcase"></i>
            <span slot="title">员工基础设置</span>
          </el-menu-item>
          <el-menu-item index="4">
            <i class="el-icon-s-cooperation"></i>
            <span slot="title">供应商基础设置</span>
          </el-menu-item>
          <el-menu-item index="5">
            <i class="el-icon-s-check"></i>
            <span slot="title">权限管理</span>
          </el-menu-item>
          <el-menu-item index="6">
            <i class="el-icon-s-promotion"></i>
            <span slot="title">公告消息</span>
          </el-menu-item>
          <el-menu-item index="7">
            <i class="el-icon-user"></i>
            <span slot="title">个人中心</span>
          </el-menu-item>
          <el-submenu index="8">
            <template slot="title">
              <i class="el-icon-setting"></i>
              <span slot="title">商品管理</span>
            </template>
            <el-menu-item-group>
              <template slot="title">商品管理</template>
              <el-menu-item index="8-1">商品入库</el-menu-item>
              <el-menu-item index="8-2">库存统计</el-menu-item>
              <el-menu-item index="8-3">配货出库</el-menu-item>
              <el-menu-item index="8-4">门店调拨</el-menu-item>
              <el-menu-item index="8-5">门店退货</el-menu-item>
              <el-menu-item index="8-6">固定编码入库</el-menu-item>
              <el-menu-item index="8-7">采购退货</el-menu-item>
              <el-menu-item index="8-8">商品拆料</el-menu-item>
            </el-menu-item-group>
          </el-submenu>
          <el-menu-item index="9">
            <i class="el-icon-s-custom"></i>
            <span slot="title">客户管理</span>
          </el-menu-item>
        </el-menu>
        <div class="navCtrl">
          <i class="el-icon-s-fold" v-if="isCollapse" @click="collapse"
             style="cursor: pointer"></i>
          <i class="el-icon-s-unfold" v-else @click="collapse"
             style="cursor: pointer"></i>
        </div>
      </el-aside>
      <el-main class="body">
        <router-view></router-view>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>

export default {
  name: 'Home',
  components: {},
  created() {
    sessionStorage.setItem("user", JSON.stringify({name: '王刚', ID: 123456}));
    this.$data.userInfo = JSON.parse(sessionStorage.getItem("user"));
  },
  data() {
    return {
      squareUrl: "https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png",
      isCollapse: true,
      userInfo: {
        name: "",
        id: 0
      },
      icon: "el-icon-s-fold",
      width: ""
    }
  },
  methods: {
    collapse: function () {
      this.$data.isCollapse = !this.$data.isCollapse;
      this.$data.width = this.$data.width === "" ? "200px" : "";
      /*this.$store.commit("increment");
      console.log(this.$store.state.count);*/
    }
  }
}
</script>

<style scoped lang="scss">
.home {
  height: 100%;

  .el-aside,
  .el-main {
    height: 100%;
    overflow: hidden auto;
  }

  .el-aside {
    background-color: rgb(84, 92, 100);
  }

  .el-container {
    height: calc(100% - 60px);
  }
}

.header {
  background-color: #545c64;
  color: #ffffff;

  .title {
    font-size: 1.2em;

    img {
      vertical-align: middle;
    }

    a {
      color: #ffffff;
      text-decoration: none;
    }
  }

  & > div {
    height: 100%;
  }

  .el-icon-s-fold,
  .el-icon-s-unfold {
    padding: 0 5px;
  }

  div {
    color: inherit;

    .dropdown {
      color: inherit;
      font-size: 1em;

      .el-dropdown-link {
        padding: 0 10px;
        display: flex;
        align-items: center;
        cursor: pointer;

        span {
          margin-right: 10px;
        }
      }
    }
  }
}

.el-menu-vertical-demo {
  height: calc(100% - 3.5em);
  overflow: hidden auto;
}

.navCtrl {
  position: fixed;
  left: 0.8em;
  bottom: 0.8em;
  font-size: 1.3em;
  color: #ffffff;
}
</style>