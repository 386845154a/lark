<template>
  <div class="layout">
    <Layout style="height: 100%">
      <Sider ref="side1" hide-trigger collapsible :collapsed-width="64" v-model="isCollapsed">
        <lark-sidebar class="sidebar-container"></lark-sidebar>
      </Sider>
      <Layout style="height: 100%">
        <Header :style="{padding: 0}" class="layout-header-bar">
          <lark-navbar></lark-navbar>
        </Header>
        <Content :style="{margin: '0px', background: '#F2F2F2', minHeight: '704px', height: '100%'}">
          <router-view></router-view>
        </Content>
      </Layout>
    </Layout>
  </div>
</template>
<script>
import LarkNavbar from "./LarkNavbar";
import LarkSidebar from "./LarkSidebar";

export default {
  name: "layout",
  components: { LarkNavbar, LarkSidebar },
  data() {
    return {
      isCollapsed: true
    };
  },
  computed: {
    menuitemClasses: function() {
      return ["menu-item", this.isCollapsed ? "collapsed-menu" : ""];
    }
  }
};
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
// @import "src/style/mixin.scss";
// *,
// *:before,
// *:after {
//   -moz-box-sizing: border-box;
//   -webkit-box-sizing: border-box;
//   box-sizing: border-box;
// }
.layout {
  // @include clearfix;
  // position: relative;
  height: 100%;
  width: 100%;
  border: 0px solid #F2F2F2;
  background: #F2F2F2;
  position: relative;
  border-radius: 1px;
  overflow: hidden;
  border: rgb(165, 165, 165);
}
.layout-header-bar {
  height: 32px;
  background: #F2F2F2;
  // box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
  -webkit-app-region: drag;
}
.menu-item span {
  display: inline-block;
  overflow: hidden;
  width: 69px;
  text-overflow: ellipsis;
  white-space: nowrap;
  vertical-align: bottom;
  transition: width 0.2s ease 0.2s;
}
.menu-item i {
  transform: translateX(0px);
  transition: font-size 0.2s ease, transform 0.2s ease;
  vertical-align: middle;
  font-size: 16px;
}
.collapsed-menu span {
  width: 0px;
  transition: width 0.2s ease;
}
.collapsed-menu i {
  transform: translateX(5px);
  transition: font-size 0.2s ease 0.2s, transform 0.2s ease 0.2s;
  vertical-align: middle;
  font-size: 22px;
}
.ivu-layout-sider {
  background: rgb(1, 68, 168) !important;
}
</style>
